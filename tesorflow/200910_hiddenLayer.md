# TENSORFLOW

<br>

### 배우는 내용
 > 히든레이어 <br>
 카테고리 분류 <br>
 isna, fillna <br>
 BatchNormalization

 <hr>

- __히든레이어__

    1. 모델의 구조

    ```
    X = tf.keras.layers.Input(shape=[13])
    H = tf.keras.layers.Dense(10, activation='swish')(X)
    Y = tf.keras.layers.Dense(1)(H)
    model = tf.keras.models.Model(X, Y)
    model.compile(loss='mse')
    ```

    2. 모델 구조 확인
    ```
    model.summary()
    ```

    3. 모델 학습
    ```
    model.fit(독립, 종속, epochs=100)
    ```

    4. 모델 이용
    ```
    model.predict(독립[:5])
    ```

    5. 히든레이어의 노드 수는 몇개가 적합할까?

    > one could probably get decent performance (even without a second optimization step) by setting the hidden layer configuration using just two rules: __(i) number of hidden layers equals one__; and __(ii) the number of neurons in that layer is the mean of the neurons in the input and output layers.__ <br> -stackoverflow

 <hr>

- __카테고리 분류__

    1. 원핫인코딩이 안된 자료 준비

    2. 숫자형, 문자형을 범주형으로 변경
    ```
    아이리스['품종'] = 아이리스['품종'].astype('category')
    ```

    3. get_dummies
    ```
    아이리스=pd.get_dummies(아이리스)
    ```

 <hr>

- __자료에서 NAN 없애기__

    1. NAN 값 체크
    ```
    아이리스.isna().sum() #NAN값이 어느 행에 몇개 있는지 가르쳐줌
    ```

    2. NAN을 평균으로 바꾸기
    ```
    mean=아이리스['꽃잎폭'].mean()
    아이리스['꽃잎폭']=아이리스['꽃잎폭'].fillna(mean)
    ```

 <hr>

- __BatchNormalization__

    1. Dense 설정
    ```
    H=tf.keras.layers.Dense(8)(X)
    ```
    2. BatchNormalization
    ```
    H=tf.keras.layers.BatchNormalization()(H)
    ```
    3. activation 설정
    ```
    H=tf.keras.layers.Activation('swish')(H)
    ```
