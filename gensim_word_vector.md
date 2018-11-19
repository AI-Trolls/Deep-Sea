# Gensim Word2Vec - word vector

- 불러와서 사용하는 기본 예제 코드
  ```python
  from gensim.models import Word2Vec
  model = Word2Vec.load("word_embedding.model")
  
  len(model.wv.vocab)
  
  model.wv.similarity('회사/NNG', '기업/NNG')
  model.wv.similarity('국립/NNG', '사립/NNG')
  print(model.wv.most_similar("국립/NNG", topn=10))
  print(model.wv.most_similar(positive=["젊은/NNG", "사람/NNG"], topn=10))
  print(model.wv.most_similar(positive=["젊은/NNG", "사람/NNG"], negative=["한국/NNG"], topn=10))

  vector = model.wv['국립/NNG']
  print(vector)
  ```

- FutureWarning: Conversion of the second argument of issubdtype from `int` to `np.signedinteger` is deprecated. In future, it will be treated as `np.int64 == np.dtype(int).type`.
  if np.issubdtype(vec.dtype, np.int):
  - pip install numpy==1.13.0
  - pip install h5py==2.8.0rc1
  - pip install --upgrade ipykernel
  - 별거 다 해봤지만 나한텐 안됨ㅠ 그래서 결국 warning을 지웠다.
  ```python
  import warnings
  warnings.filterwarnings('ignore')
  ```
