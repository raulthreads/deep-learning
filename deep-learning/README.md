# Deep-learning-challenge

## Report and Analysis

The purpose of our analysis is to help a nonprofit foundation Alphabet Soup select whether or not their applicants for funding would be successful in their ventures. We will be creating a binary classifier that can predict their success outcome, using features provided in the dataset.

Data Preprocessing

What variable(s) are the target(s) for your model?

As target we used the "IS_SUCCESSFUL" variable (see below with the number of unique values for the target)
    IS_SUCCESSFUL                2

What variable(s) are the features for your model?

Whereas for the features we used the rest of the features, after dropping ID columns such as "EIN" and "NAME", not relevant in our analysis. (see below with the number of unique values for each feature)
    APPLICATION_TYPE            17
    AFFILIATION                  6
    CLASSIFICATION              71
    USE_CASE                     5
    ORGANIZATION                 4
    STATUS                       2
    INCOME_AMT                   9
    SPECIAL_CONSIDERATIONS       2
    ASK_AMT                   8747

What variable(s) should be removed from the input data because they are neither targets nor features?
ID columns such as "EIN" and "NAME" were dropped as they were neither targets nor features.

Compiling, Training, and Evaluating the Model

How many neurons, layers, and activation functions did you select for your neural network model, and why?

In our model initially, we used 2 hidden layers with 80 and 30 neurons respectively, using the "relu" activation functions in the hidden layers and "sigmoid" on the output layer. We also used the length of the training features as number of input features.

Were you able to achieve the target model performance?

    Loss: 0.556739866733551, Accuracy: 0.7295626997947693

Our model only reached a 72.96% accuracy. Which means there is room for improvement.

What steps did you take in your attempts to increase model performance?

As an attempt to increase our model accuracy, the following attempts were made with the indicated accuracy for each;


ATTEMPT #1:
We pre-processed our data similarly to the initial model, and changed the number of nodes for each of the 2 layers to 100 and 50 according.
As a result we got;
1st attempt Loss: 0.5588715076446533, 1st attempt Accuracy: 0.7289795875549316

ATTEMPT #2:
Here again, we pre-processed the data same as previously but increased the number of layers and nodes in each layer in our model.
    number_input_features_2 = len(X_train[0])
    hidden_nodes_layer1_2 =  100
    hidden_nodes_layer2_2 = 100
    hidden_nodes_layer3_2 = 100
    hidden_nodes_layer4_2 = 100
    hidden_nodes_layer5_2 = 100

As a result we got;
2nd attempt Loss: 0.5765700936317444, 2nd attempt Accuracy: 0.7306122183799744

ATTEMPT #3:
Here again, we pre-processed the data same as previously but changed activation functions for the hidden layers in our model.
    # 1st hidden layer
    nn.add(tf.keras.layers.Dense(units= hidden_nodes_layer1_3, activation="tanh", input_dim=number_input_features_3))

    # 2nd hidden layer
    nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer2_3, activation="tanh"))

    # Output layer
    nn.add(tf.keras.layers.Dense(units=1, activation="sigmoid"))

As a result we got;
3rd attempt Loss: 0.557525098323822, 3rd attempt Accuracy: 0.7302623987197876  

ATTEMPT #4:
Once again, data was pre-processed as before but decreased the epochs while keeping everything else the same.
    # Training the model
    fit_model = nn.fit(X_train_scaled,y_train,epochs=70)
As a result we got;
4th attempt Loss: 0.5535637140274048, 4th attempt Accuracy: 0.7278134226799011

ATTEMPT #5:
This time, we changed our data pre-processing by increasing the rare occurences in "APPLICATION_TYPE", "CLASSIFICATION" and "ASK_AMT" columns, while keeping the rest of the model similar to the initial model.

As a result we got;
5th attempt Loss: 0.5579429268836975, 5th attempt Accuracy: 0.7300291657447815
