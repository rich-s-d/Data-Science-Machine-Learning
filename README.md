## conda cheatsheet
https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf

## setting up the conda environment
yml file provided.

# sklearn - tabular data machine learning

```py
import sklearn
sklearn.show_versions()

from sklearn.datasets import load_boston

from sklearn.emsemble import RandomForestClassifier
from sklearn.emsemble import RandomForestRegressor
from sklearn.svm import LinearSVC

from sklearn.model_selection import train_test_split

# classification metrics
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score
from sklearn.metrics import absolute_mean_error
from sklearn.model_selection import cross_val_score
## binary metrics
from sklearn.metrics import roc_curve # fpr, tpr, thresholds = roc_curve(y_test, y_probs_positive)
from sklearn.metrics import roc_auc_score # gives area under the roc_curve.

# regression metrics


# preprocessing
from sklearn.preprocessing import OneHotEncoder
pd.get_dummies()
from sklearn.compose import ColumnTransformer
from sklearn.impute import SimpleImputer
imputer.fit_transform()
imputer.transform()

np.random.seed(42)

# create data
df.pop()
df.drop('column', axis=1)
df.isna().sum()
df.dropna(inplace=True)

# model attributes
model.get_params()
model.fit()
model.predict()
model.predict_proba()
model.score()

df.shape


# import matplotlib.pyplot as plt

def plot_roc_curve(fpr, tpr):
    '''
    Plots a roc curve given the false positive rate (fpr) and the true positive rate (tpr) of model.
    '''
    # plot the roc curve
    plt.plot(fpr, tpr, color="orange", label="ROC")
    # plot line with no predictive power (baseline)
    plt.plot([0, 1], [0, 1], color="darkblue", linestyle="--", label="Guessing")
    #custimise the plot 
    plt.xlabel("False Positive Rate (fpr)")
    plt.ylabel("True Positive Rate (tpr)")
    plt.title("Receiver Operating Characteristics (ROC) Curve")
    plt.legend()
    plt.show()



# improve a model 
## try different hyperparameters
np.random.seed(42)
for i in range(10, 100, 10):
    print(f"Trying model with {i} estimators...")
    clf = RandomForestClassifier(i).fit(x_train, y_train)
    print(f"Model accuracy on test set: {clf.score(x_test, y_test) *100:.2f}%")
    print("")
    
# save a module and load it
import pickle

pickle.dump(clf, open("random_forest_model_1.pk1", "wb"))

loaded_model = pickle.load(open("random_forest_model_1.pk1", "rb"))
loaded_model.score(x_test, y_test)
```
