# Classificação
## KNN
- Definido pelos vizinho mais proximos
- sklearn.neighbors.KNeighborsClassifier
- KNeighborsClassifier(n_neighbors=5 , *, weights='uniform', algorithm='auto', leaf_size=30, p=2, metric='minkowski', metric_params=None, n_jobs=None)
  - n_neighbors: N° De vizinhos a serem levados em consideração
  - metric: Tipo de distancia que sera utilizado
- ![image](https://webdesignemfoco.com/img/files/ckfinder/images/exemplo-de-knn-python-2.png)

## Árvore de Classificação
- Define Como uma arvore de escolhas
- sklearn.tree.DecisionTreeClassifier
- DecisionTreeClassifier(*, criterion='gini', splitter='best', max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features=None, random_state=None, max_leaf_nodes=None, min_impurity_decrease=0.0, class_weight=None, ccp_alpha=0.0)
  - ...
- ![image](https://github.com/Patrick-Setubal/Data_Science_Analytics/assets/125592481/9f26ebdd-29f8-4e06-8677-ec81f7dfa5ad)

## Naive Bayes GaussianNB
- Analisa pela probailidade de cada Features
- sklearn.naive_bayes.GaussianNB
- GaussianNB(*, priors=None, var_smoothing=1e-09)
  - ...
- ![image](https://github.com/Patrick-Setubal/Data_Science_Analytics/assets/125592481/41106ae0-c802-4899-8637-1b6a65036948)


## SVC
- Cria Dimenções para poder separas os dados
- sklearn.svm.SVC
- SVC(*, C=1.0, kernel='rbf', degree=3, gamma='scale', coef0=0.0, shrinking=True, probability=False, tol=0.001, cache_size=200, class_weight=None, verbose=False, max_iter=-1, decision_function_shape='ovr', break_ties=False, random_state=None)
  - ...
- ![image](https://github.com/Patrick-Setubal/Data_Science_Analytics/assets/125592481/683d13d3-e314-43c8-ab17-b48426379b1d)

## Random ForestCLassifier
- Pontuações aleatorias para cada descição e melhorando elas a cada tentativa
- sklearn.ensemble.RandomForestClassifier
![image](https://github.com/Patrick-Setubal/Data_Science_Analytics/assets/125592481/f78fd49a-0343-467d-bf79-3cb07a723c3f)

