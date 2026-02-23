# Developing a Neural Network Classification Model

## AIM

To develop a neural network classification model for the given dataset.

## Problem Statement

An automobile company has plans to enter new markets with their existing products. After intensive market research, they’ve decided that the behavior of the new market is similar to their existing market.

In their existing market, the sales team has classified all customers into 4 segments (A, B, C, D ). Then, they performed segmented outreach and communication for a different segment of customers. This strategy has work exceptionally well for them. They plan to use the same strategy for the new markets.

You are required to help the manager to predict the right group of the new customers.

## Neural Network Model

<img width="832" height="834" alt="image" src="https://github.com/user-attachments/assets/eb33c3b3-69b8-437a-82b4-e892642f907b" />

## DESIGN STEPS
3 STEP 1:
Import necessary libraries and load the dataset.

# STEP 2:
Encode categorical variables and normalize numerical features.

# STEP 3:
Split the dataset into training and testing subsets.

# STEP 4:
Design a multi-layer neural network with appropriate activation functions.

# STEP 5:
Train the model using an optimizer and loss function.

# STEP 6:
Evaluate the model and generate a confusion matrix.

# STEP 7:
Use the trained model to classify new data samples.

# STEP 8:
Display the confusion matrix, classification report, and predictions.


## PROGRAM

### Name: JANANI S
### Register Number: 212223230086

```python
class PeopleClassifier(nn.Module):
    def __init__(self, input_size):
        super(PeopleClassifier, self).__init__()
        self.fc1=nn.Linear(input_size,16)
        self.fc2=nn.Linear(16,8)
        self.fc3=nn.Linear(8,4)


    def forward(self, x):
      x=F.relu(self.fc1(x))
      x=F.relu(self.fc2(x))
      x=self.fc3(x)
      return x
       

```
```python
# Initialize the Model, Loss Function, and Optimizer
model =PeopleClassifier(input_size=X_train.shape[1])
criterion =nn.CrossEntropyLoss()
optimizer =optim.Adam(model.parameters(), lr=0.01)

```
```python
def train_model(model, train_loader, criterion, optimizer, epochs):
   for epoch in range(epochs):
    model.train()
    for X_batch, y_batch in train_loader:
      optimizer.zero_grad()
      outputs = model(X_batch)
      loss = criterion(outputs, y_batch)
      loss.backward ()
      optimizer.step()

    if (epoch + 1) % 10 == 0:
        print(f'Epoch [{epoch+1}/{epochs}], Loss: {loss.item():.4f}')
```



## Dataset Information

<img width="1266" height="253" alt="image" src="https://github.com/user-attachments/assets/4868bfa5-23fa-458c-981f-d86e0d347e20" />



## OUTPUT

### Confusion Matrix and Classification report

<img width="995" height="695" alt="image" src="https://github.com/user-attachments/assets/2572730f-8034-4efd-9868-1db9784814e6" />


<img width="707" height="526" alt="image" src="https://github.com/user-attachments/assets/50357ca0-8fb4-4f03-8f24-afca5279613e" />

```
# Prediction for a sample input
sample_input = X_test[12].clone().unsqueeze(0).detach().type(torch.float32)
with torch.no_grad():
    output = model(sample_input)
    # Select the prediction for the sample (first element)
    predicted_class_index = torch.argmax(output[0]).item()
    predicted_class_label = label_encoder.inverse_transform([predicted_class_index])[0]
print("Name: JANANI S")
print("Register No: 212223230086")
print(f'Predicted class for sample input: {predicted_class_label}')
print(f'Actual class for sample input: {label_encoder.inverse_transform([y_test[12].item()])[0]}')
```

<img width="850" height="127" alt="image" src="https://github.com/user-attachments/assets/1901af4d-b888-4cd3-b1b9-d200e3a590be" />




## RESULT
Thus, a neural network classification model for the given dataset as been created successfully.

