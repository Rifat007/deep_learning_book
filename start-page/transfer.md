# ট্রান্সফার লার্নিং, ‘প্রি-ট্রেইনড’ অক্সফোর্ড ইউনিভার্সিটি ভিজ্যুয়াল জিওমেট্রি গ্রূপের vgg16 ডেটাসেট

{% hint style="info" %}
আমরা বই পড়ছি, নোটবুক কেন পড়বো? 

নোটবুক সবসময় আপডেটেড। এই বই থেকেও। 

যেহেতু গিটবুকে নোটবুক ঠিকমতো রেন্ডার হয়না, সেকারণে গুগল কোলাব এবং গিটহাবে দেখা উচিৎ। গিটহাব লিংক: 

নিজে নিজে প্র্যাকটিস করুন: [https://github.com/raqueeb/TensorFlow2/blob/master/tf2\_transfer\_learning\_v3.ipynb](https://github.com/raqueeb/TensorFlow2/blob/master/tf2_transfer_learning_v3.ipynb) এবং [https://nbviewer.jupyter.org/github/raqueeb/TensorFlow2/blob/master/tf2\_transfer\_learning\_v3.ipynb](https://nbviewer.jupyter.org/github/raqueeb/TensorFlow2/blob/master/tf2_transfer_learning_v3.ipynb)

কোলাব লিংক: [https://colab.research.google.com/github/raqueeb/TensorFlow2/blob/master/tf2\_transfer\_learning\_v3.ipynb](https://colab.research.google.com/github/raqueeb/TensorFlow2/blob/master/tf2_transfer_learning_v3.ipynb)
{% endhint %}

## ট্রান্সফার লার্নিং এবং ‘প্রি-ট্রেইনড’ অক্সফোর্ড ইউনিভার্সিটি’র ভিজ্যুয়াল জিওমেট্রি গ্রূপের vgg16 ডাটাসেট

মানুষের মধ্যেই সবচেয়ে বেশি ট্রান্সফার লার্নিং ব্যাপারটা লক্ষ্য করা যায়। যেমন, আমরা একটা জিনিস শিখি তবে সেই জিনিসটা যে অন্য কোন কাজে লাগে না সেটা একদম ঠিক নয়। ধরা যাক, এক সময় আমি অংক, অ্যালজেবরা শিখেছি, পাশাপাশি পরিসংখ্যান শিখেছি পরীক্ষায় পাশ করার জন্য। এখন সেই জ্ঞানগুলো ট্রান্সফার হয়েছে মেশিন লার্নিং শিখতে গিয়ে। অংক,অ্যালজেবরা এবং পরিসংখ্যান শেখাটা বৃথা যায়নি। কারণ, আমাকে মেশিন লার্নিং একেবারে কেঁচে গণ্ডূষ করে শুরু করতে হয়নি, কারণ অংক এবং পরিসংখ্যান পাশাপাশি অ্যালজেবরা এই মেশিন লার্নিং শেখার জন্য সাহায্য করেছে। সে কারণেই বলা হয় যদিও একটা কাজের জন্য আমরা কোন কিছু শিখি, দেখা যায় পরে ওই শেখাটা অন্য কাজে লাগছে। এর অর্থ হচ্ছে আমরা অতীতে যা কিছু শিখেছি সেটা এখন কাজে লাগছে নতুন কিছু শিখতে। সেখানে এক ডোমেইন থেকে আরেক ডোমেইনে জ্ঞানটা ট্রান্সফার হচ্ছে।

ছোটবেলায় সাইকেল চালানো শিখেছিলাম বলেই মোটরসাইকেল ধরতে খুব একটা সমস্যা হয়নি। আবার কেউ যদি মোটরসাইকেল চালাতে পারেন তাহলে তার জন্য গাড়ি চালানোর শুরুর ব্যাপারগুলো ধরতে সে রকম সমস্যা হবার কথা না। বাচ্চারা যখন কোন মোবাইল ডিভাইস ব্যবহার করা শেখে, তারা হঠাৎ করে আইপ্যাড পেলে তাদের পুরনো জ্ঞান দিয়েই চালিয়ে নেয় নতুন জিনিস। এর অর্থ হচ্ছে একটার নলেজ আরেকটাতে ট্রান্সফার করা যাচ্ছে। এই একই জিনিস ঘটছে ডিপ লার্নিং এর আরেকটা নতুন ধারণায়। ‘ট্রান্সফার লার্নিং’। একটা কাজে একটা মডেলকে ট্রেইন করা হলে সেটাকে যে পাশাপাশি আর একটা কাজে ব্যবহার করা যাবে না সেটা ঠিক নয়। আমরা একটা ডিপ লার্নিং মডেলকে যদি ‘ইমেজ’ রিলেটেড ব্যাপারে ট্রেনিং করাই, তাহলে ওই কাজের কাছাকাছি আরেকটা কাজে ব্যবহার করা যাবে। ওই দুটো কাজের মধ্যে যত ‘সিমিলারিটি’ আছে ততোই মডেল গুলোর মধ্যে লার্নিং গুলোকে ট্রান্সফার করা সহজ হবে। শুরুতে একটা কাজের জন্য আমরা একদম গোড়া থেকে ট্রেইনিং করলেও পরের কাছাকাছি সেই কাজের জন্য একদম গোড়া থেকে ট্রেনিং করানোর প্রয়োজন নেই। এটাই ট্রান্সফার লার্নিং।

গোড়ার দিকে মেশিন লার্নিং এবং ডিপ লার্নিং অ্যালগরিদমগুলোকে এমনভাবে তৈরি করা হয়েছিল যাতে সে একটা স্পেসিফিক কাজ করতে পারে। আবার এই মডেলগুলোকে একেবারে গোড়া থেকে তৈরি করতে হতো যখন তাদের ফিচার স্পেস ডিস্ট্রিবিউশনে কোন পরিবর্তন আসতো। এখন দেখা যাচ্ছে ফিচার স্পেসে পরিবর্তন আসলেও কাছাকাছি কাজে একটার লার্নিং আরেকটাতে পাঠানো যাচ্ছে। সে কারণে আমরা গত চ্যাপ্টারে আলাপ করেছি ‘প্রি-ট্রেইনড’ মডেল নিয়ে। ‘প্রি-ট্রেইনড’ মডেল হচ্ছে একটা ‘স্টোরকৃত’ বা ‘সেভকৃত’ মডেল যাকে আগেই ট্রেনিং করানো হয়েছিল বিশাল আরেকটা ডাটাসেটের উপর। আমরা সেই মডেলকে অন্য আরেকটা কাজে সরাসরি অথবা ‘ট্রান্সফার লার্নিং’ এর মাধ্যমে আগের মডেলের পুরো বা কিছু অংশ নিয়ে নতুন মডেলকে কাস্টমাইজ করবো। আমাদের ‘প্রি-ট্রেইনড’ মডেল যদি কোটি কোটি ইমেজের উপর ট্রেনিং করানো থাকে, তাহলে সেই মডেলকে দিয়ে নতুন কাজে ওই ছবিগুলোর ‘লার্নিং’ ব্যবহার করা যাবে। ‘ট্রান্সফার লার্নিং’ এর সবচেয়ে বড় ব্যবহার হচ্ছে যখন আমাদের হাতে পর্যাপ্ত ডাটা থাকে না ট্রেনিং করানোর জন্য। সেই জ্ঞানকে নিয়ে আসছি আগের প্রি-ট্রেইনড মডেলের প্রাপ্ত জ্ঞান থেকে।

ধরা যাক আমাদের কাছে একটা ‘প্রি-ট্রেইনড’ মডেল আছে যেগুলো প্রায় ১০০০ ছবি ক্যাটাগরিতে কাজ করেছে। এখন আমার নতুন কাজে যেখানে মাত্র দুটো ছবির ক্যাটাগরি নিয়ে কাজ করছি সেখানে আগের একটা ‘প্রি-ট্রেইনড’ মডেল কোন রকম পরিবর্তন ছাড়াই ব্যবহার করা যায়। আসল কথা হচ্ছে আমাদের ডিপ লার্নিং মডেলগুলো যে ফিচার ম্যাপ তৈরি করে - সেগুলোকে নতুন কাজে আবার গোড়া থেকে ‘ফিচার ম্যাপ’ তৈরি না করে শেষে ক্লাসিফায়ার অংশটুকু ফেলে দিয়ে নতুন ক্লাসিফায়ার যোগ করলেই কাজ হয়ে যায়। মানে একজনের শরীর, আরেকজনের মাথা। মজার কথা, জিনিসটা কাজ করে।

```python
try:
  # শুধুমাত্র টেন্সর-ফ্লো ২.x ব্যবহার করবো 
  %tensorflow_version 2.x
except Exception:
  pass

import tensorflow as tf
keras = tf.keras
```

```text
TensorFlow 2.x selected.
```

```python
# কিছু হেল্পার লাইব্রেরি ব্যবহার করছি

import tensorflow as tf
from tensorflow.keras import layers
import tensorflow_datasets as tfds
import matplotlib.pylab as plt
```

```python
# টেন্সর-বোর্ড ব্যবহার করছি, এক্সটেনশন এবং লগ ডিরেক্টরি দেখিয়ে দিচ্ছি

%load_ext tensorboard
LOG_DIR = './log'
```

```python
# আগের মতো বিড়াল এবং কুকুরের ডেটাসেট নিয়ে কাজ করছি, দেখে নিন 'গ্লোবাল এভারেজ পুলিং' 
# বিস্তারিত বলেছি আগের চ্যাপ্টারে, স্প্লিট হচ্ছে ৮০ ট্রেনিং, ১০ ভ্যালিডেশন, ১০ টেস্টসেট শতাংশে

split = (80, 10, 10)
splits = tfds.Split.TRAIN.subsplit(weighted=split)

(cat_train, cat_valid, cat_test), info = tfds.load('cats_vs_dogs', split=list(splits), with_info=True, as_supervised=True)
```

```text
[1mDownloading and preparing dataset cats_vs_dogs (786.68 MiB) to /root/tensorflow_datasets/cats_vs_dogs/2.0.1...[0m



HBox(children=(IntProgress(value=1, bar_style='info', description='Dl Completed...', max=1, style=ProgressStyl…



HBox(children=(IntProgress(value=1, bar_style='info', description='Dl Size...', max=1, style=ProgressStyle(des…


/usr/local/lib/python3.6/dist-packages/urllib3/connectionpool.py:847: InsecureRequestWarning: Unverified HTTPS request is being made. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/latest/advanced-usage.html#ssl-warnings
  InsecureRequestWarning)








HBox(children=(IntProgress(value=1, bar_style='info', max=1), HTML(value='')))


WARNING:absl:1738 images were corrupted and were skipped





HBox(children=(IntProgress(value=0, description='Shuffling...', max=20, style=ProgressStyle(description_width=…


WARNING:tensorflow:From /usr/local/lib/python3.6/dist-packages/tensorflow_datasets/core/file_format_adapter.py:209: tf_record_iterator (from tensorflow.python.lib.io.tf_record) is deprecated and will be removed in a future version.
Instructions for updating:
Use eager execution and: 
`tf.data.TFRecordDataset(path)`


WARNING:tensorflow:From /usr/local/lib/python3.6/dist-packages/tensorflow_datasets/core/file_format_adapter.py:209: tf_record_iterator (from tensorflow.python.lib.io.tf_record) is deprecated and will be removed in a future version.
Instructions for updating:
Use eager execution and: 
`tf.data.TFRecordDataset(path)`



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1164, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1164, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…



HBox(children=(IntProgress(value=1, bar_style='info', description='Reading...', max=1, style=ProgressStyle(des…



HBox(children=(IntProgress(value=0, description='Writing...', max=1163, style=ProgressStyle(description_width=…


[1mDataset cats_vs_dogs downloaded and prepared to /root/tensorflow_datasets/cats_vs_dogs/2.0.1. Subsequent calls will reuse this data.[0m
```

```python
# একটু দেখি ডেটাসেটে কি আছে?

get_label_name = info.features['label'].int2str
for image, label in cat_test.take(2):
  plt.figure()
  plt.imshow(image)
  plt.title(get_label_name(label))
  image_ = image
```

![png](../.gitbook/assets/output_5_0.png)

![png](../.gitbook/assets/output_5_1.png)

```python
# এই অবজেক্টগুলো (ইমেজ, লেবেল) জোড়ায় আছে, শেপ, ৩ চ্যানেল এবং লেবেল স্কেলারে আছে

print(cat_train)
print(cat_valid)
print(cat_test)
```

```text
<_OptionsDataset shapes: ((None, None, 3), ()), types: (tf.uint8, tf.int64)>
<_OptionsDataset shapes: ((None, None, 3), ()), types: (tf.uint8, tf.int64)>
<_OptionsDataset shapes: ((None, None, 3), ()), types: (tf.uint8, tf.int64)>
```

```python
# ইমেজ প্রি-প্রসেস করছি, ১৬০ পিক্সেলে

# IMAGE_SIZE = 100
# def pre_process_image(image, label):
# image = tf.cast(image, tf.float32)
# image = image / 255.0
# image = tf.image.resize(image, (IMAGE_SIZE, IMAGE_SIZE))
# return image, label

IMAGE_SIZE = 160 

def pre_process_image(image, label):
  image = tf.cast(image, tf.float32)
  image = (image/127.5) - 1
  image = tf.image.resize(image, (IMAGE_SIZE, IMAGE_SIZE))
  return image, label
```

```python
# এই একই ফাংশনকে ব্যবহার করছি ডেটাসেটের প্রতিটা আইটেম নিয়ে, ম্যাপ মেথডে 

# TRAIN_BATCH_SIZE = 64
# cat_train = cat_train.map(pre_process_image).shuffle(1000).repeat().batch(TRAIN_BATCH_SIZE)
# cat_valid = cat_valid.map(pre_process_image).repeat().batch(1000)

# কিভাবে 'শাফল' করবে এবং ব্যাচ সাইজও বলে দিচ্ছি

BATCH_SIZE = 32
SHUFFLE_BUFFER_SIZE = 1000

cat_train = cat_train.map(pre_process_image)
cat_valid = cat_valid.map(pre_process_image)
cat_test = cat_test.map(pre_process_image)
```

```python
# আলাদাভাবে প্রতিটা ব্যাচ

train_batches = cat_train.shuffle(SHUFFLE_BUFFER_SIZE).batch(BATCH_SIZE)
validation_batches = cat_valid.batch(BATCH_SIZE)
test_batches = cat_test.batch(BATCH_SIZE)
```

```python
# ব্যাচ, ইমেজ সাইজ, ইমেজ সাইজ, কালার চ্যানেল

for image_batch, label_batch in train_batches.take(1):
   pass

image_batch.shape
```

```text
TensorShape([32, 160, 160, 3])
```

## একটা কনভলিউশন বেইজ, আরেকটা ক্লাসিফায়ার হেড

একটা ‘কনভলিউশনাল নিউরাল’ নেটওয়ার্কে কি আছে? একটা কনভলিউশন বেইজ, আরেকটা ক্লাসিফায়ার হেড। বেশিরভাগ সময় ‘প্রি-ট্রেইনড’ মডেলের কনভলিউশন বেইজ ঠিক রেখে নতুন কাজের নতুন ক্লাসিফায়ার হেড যোগ করলেই ট্রান্সফার লার্নিং এর ব্যবহার দেখতে পারি সহজেই। ট্রান্সফার লার্নিং এর শুরুতেই আমাদের আগের অন্য কাজের জন্য তৈরি মডেলকে ব্যবচ্ছেদ করবো আমরা। তখন বুঝব সেই ‘প্রি-ট্রেইনড’ মডেলের কতটুকু আমরা ‘আনকোরা’ ব্যবহার করব আর কতটুকু নতুন করে ট্রেইন করে নেব সেটা হাতেকলমে দেখবো সামনে।

অনেক গল্প হল, এই মুহূর্তে আমরা একটা ‘প্রি-ট্রেইনড’ মডেলের কিভাবে কাস্টমাইজেশন করব সেটা নিয়ে আলাপ করছি এখানে।

```python
# মডেলের মাথা

head = tf.keras.Sequential()
head.add(layers.Conv2D(32, (3, 3), input_shape=(IMAGE_SIZE, IMAGE_SIZE, 3)))
head.add(layers.BatchNormalization())
head.add(layers.Activation('relu'))
head.add(layers.MaxPooling2D(pool_size=(2, 2)))

head.add(layers.Conv2D(32, (3, 3)))
head.add(layers.BatchNormalization())
head.add(layers.Activation('relu'))
head.add(layers.MaxPooling2D(pool_size=(2, 2)))

head.add(layers.Conv2D(64, (3, 3)))
head.add(layers.BatchNormalization())
head.add(layers.Activation('relu'))
head.add(layers.MaxPooling2D(pool_size=(2, 2)))
```

```python
# average_pool = tf.keras.Sequential()
# average_pool.add(layers.AveragePooling2D())
# average_pool.add(layers.Flatten())
# average_pool.add(layers.Dense(1, activation='sigmoid'))

# গ্লোবাল এভারেজ পুল, এর কাজ হচ্ছে ফিচারগুলোকে একটা ১২৮০ এলিমেন্ট ভেক্টরে কনভার্ট করবে প্রতিটা ইমেজে
average_pool = tf.keras.layers.GlobalAveragePooling2D()
# একটা করে প্রেডিকশন প্রতিটা ইমেজে, এক্টিভেশন ফাংশন দরকার নেই, যেহেতু পজিটিভ সংখ্যা ১, নেগেটিভ সংখ্যা ০
prediction = keras.layers.Dense(1)
```

১. ‘প্রি-ট্রেইনড’ মডেল থেকে ফিচার এক্সট্রাকশন: আমরা রিপ্রেজেন্টেশন লার্নিং এর মাধ্যমে আগের নেটওয়ার্ক থেকে শিখে সেটা দিয়ে নতুন নেটওয়ার্কের দরকারি ফিচারগুলোকে এক্সট্রাক্ট করব নতুন ডাটা থেকে। এর শেষে আমরা একটা নতুন ক্লাসিফায়ার হেড যোগ করে দেব যাকে ট্রেনিং করালেই বাকি মডেলকে আনকোরা রাখলেও কাজ হয়ে যাবে। এর অর্থ হচ্ছে আমাদের আগের প্রি-ট্রেইনড মডেলকে ব্যবহার করছি নতুন একটা কাজে। আমরা কিন্তু পুরো মডেলকে ট্রেইন করছিনা, শুধুমাত্র দরকারি ক্লাসিফায়ার হেডকে সেই কয়েকটা ক্লাসিফিকেশন কাজের জন্য ট্রেইন করলেই চলছে। পেছনে আগের মডেলের কনভলিউশন বেইজ একই থাকছে। মানে এক নেটওয়ার্ক থেকে কনভলিউশন বেইজ এবং নতুন কাজের নেটওয়ার্ক ক্লাসিফায়ার হেড \(নতুন কাজের শেষ অংশ\) যোগ করে দিলেই কাজ হয়ে যাবে।

```python
# তিনটা জিনিস যোগ করে মডেল তৈরি
standard_model = tf.keras.Sequential([
    head, 
    average_pool,
    prediction
])
```

```python
# মাত্র ২টা ক্লাস, সেকারণে লস 'binary_crossentropy'

# standard_model.compile(optimizer=tf.keras.optimizers.Adam(),
#              loss='binary_crossentropy',
#              metrics=['accuracy'])

base_learning_rate = 0.0001
standard_model.compile(optimizer=tf.keras.optimizers.RMSprop(lr=base_learning_rate),
              loss='binary_crossentropy',
              metrics=['accuracy'])
```

```python
# টেন্সর-বোর্ডে দেখবো না? আগে আলাপ করেছি

callbacks = [tf.keras.callbacks.TensorBoard(log_dir='./log/standard_model', update_freq='batch')]
```

```python
# আমাদের ছবিগুলোকে গুনে নেই ট্রেইন, ভ্যালিডেশন এবং টেস্টসেটের জন্য

# standard_model.fit(cat_train, steps_per_epoch = 23262//TRAIN_BATCH_SIZE, epochs=7, 
#               validation_data=cat_valid, validation_steps=10, callbacks=callbacks)

num_train, num_val, num_test = (
  info.splits['train'].num_examples*weight/10
  for weight in split
)
```

```python
# শুরুর ইপক এবং প্রতিটা ইপকের স্টেপ বলে দেই

initial_epochs = 10
steps_per_epoch = round(num_train)//BATCH_SIZE
validation_steps = 20

loss0,accuracy0 = standard_model.evaluate(validation_batches, steps = validation_steps)
```

```text
20/20 [==============================] - 6s 285ms/step - loss: 1.2152 - accuracy: 0.5125
```

```python
# ধারণা করি শুরুর অ্যাক্যুরেসি আর লসের অংক

print("initial loss: {:.2f}".format(loss0))
print("initial accuracy: {:.2f}".format(accuracy0))
```

```text
initial loss: 1.22
initial accuracy: 0.51
```

```python
# মডেল ট্রেনিং, ব্যাচে, স্ট্যান্ডার্ড মডেল, ট্রান্সফার লার্নিং ছাড়া
# কলব্যাক, টেন্সরবোর্ডের জন্য

history = standard_model.fit(train_batches,
                    epochs=initial_epochs,
                    validation_data=validation_batches,
                    callbacks=callbacks)
```

```text
Epoch 1/10
      1/Unknown - 5s 5s/step - loss: 2.6915 - accuracy: 0.5625WARNING:tensorflow:Method (on_train_batch_end) is slow compared to the batch update (0.235030). Check your callbacks.


WARNING:tensorflow:Method (on_train_batch_end) is slow compared to the batch update (0.235030). Check your callbacks.


      2/Unknown - 5s 3s/step - loss: 2.1321 - accuracy: 0.4688WARNING:tensorflow:Method (on_train_batch_end) is slow compared to the batch update (0.228094). Check your callbacks.


WARNING:tensorflow:Method (on_train_batch_end) is slow compared to the batch update (0.228094). Check your callbacks.


582/582 [==============================] - 101s 174ms/step - loss: 0.6875 - accuracy: 0.6331 - val_loss: 0.0000e+00 - val_accuracy: 0.0000e+00
Epoch 2/10
582/582 [==============================] - 97s 167ms/step - loss: 0.6353 - accuracy: 0.6803 - val_loss: 0.6358 - val_accuracy: 0.7043
Epoch 3/10
582/582 [==============================] - 97s 166ms/step - loss: 0.6132 - accuracy: 0.7012 - val_loss: 0.5828 - val_accuracy: 0.7237
Epoch 4/10
582/582 [==============================] - 96s 165ms/step - loss: 0.6060 - accuracy: 0.7082 - val_loss: 0.7234 - val_accuracy: 0.6552
Epoch 5/10
582/582 [==============================] - 96s 166ms/step - loss: 0.6055 - accuracy: 0.7168 - val_loss: 0.6674 - val_accuracy: 0.6901
Epoch 6/10
582/582 [==============================] - 97s 167ms/step - loss: 0.5945 - accuracy: 0.7251 - val_loss: 0.5868 - val_accuracy: 0.7366
Epoch 7/10
582/582 [==============================] - 97s 166ms/step - loss: 0.5907 - accuracy: 0.7294 - val_loss: 0.6013 - val_accuracy: 0.7310
Epoch 8/10
582/582 [==============================] - 96s 164ms/step - loss: 0.5897 - accuracy: 0.7298 - val_loss: 0.6565 - val_accuracy: 0.6810
Epoch 9/10
582/582 [==============================] - 96s 165ms/step - loss: 0.5854 - accuracy: 0.7337 - val_loss: 0.6246 - val_accuracy: 0.7004
Epoch 10/10
582/582 [==============================] - 97s 166ms/step - loss: 0.5960 - accuracy: 0.7364 - val_loss: 0.5645 - val_accuracy: 0.7539
```

```python
# টেন্সরবোর্ড চালু করছি, তবে শেষে দেখলে ভালো

%tensorboard --logdir log/
```

  
  \(function\(\) {  
    window.TENSORBOARD\_ENV = window.TENSORBOARD\_ENV \|\| {};  
    window.TENSORBOARD\_ENV\["IN\_COLAB"\] = true;  
    document.querySelector\("base"\).href = "https://localhost:6006";  
    function fixUpTensorboard\(root\) {  
      const tftb = root.querySelector\("tf-tensorboard"\);  
      // Disable the fragment manipulation behavior in Colab. Not  
      // only is the behavior not useful \(as the iframe's location  
      // is not visible to the user\), it causes TensorBoard's usage  
      // of \`window.replace\` to navigate away from the page and to  
      // the \`localhost:&lt;port&gt;\` URL specified by the base URI, which  
      // in turn causes the frame to \(likely\) crash.  
      tftb.removeAttribute\("use-hash"\);  
    }  
    function executeAllScripts\(root\) {  
      // When \`script\` elements are inserted into the DOM by  
      // assigning to an element's \`innerHTML\`, the scripts are not  
      // executed. Thus, we manually re-insert these scripts so that  
      // TensorBoard can initialize itself.  
      for \(const script of root.querySelectorAll\("script"\)\) {  
        const newScript = document.createElement\("script"\);  
        newScript.type = script.type;  
        newScript.textContent = script.textContent;  
        root.appendChild\(newScript\);  
        script.remove\(\);  
      }  
    }  
    function setHeight\(root, height\) {  
      // We set the height dynamically after the TensorBoard UI has  
      // been initialized. This avoids an intermediate state in  
      // which the container plus the UI become taller than the  
      // final width and cause the Colab output frame to be  
      // permanently resized, eventually leading to an empty  
      // vertical gap below the TensorBoard UI. It's not clear  
      // exactly what causes this problematic intermediate state,  
      // but setting the height late seems to fix it.  
      root.style.height = \`${height}px\`;  
    }  
    const root = document.getElementById\("root"\);  
    fetch\("."\)  
      .then\(\(x\) =&gt; x.text\(\)\)  
      .then\(\(html\) =&gt; void \(root.innerHTML = html\)\)  
      .then\(\(\) =&gt; fixUpTensorboard\(root\)\)  
      .then\(\(\) =&gt; executeAllScripts\(root\)\)  
      .then\(\(\) =&gt; setHeight\(root, 800\)\);  
  }\)\(\);  
 আমরা আজকে একটা বেইজ মডেল তৈরি করব অক্সফোর্ড ইউনিভার্সিটি’র ভিজ্যুয়াল জিওমেট্রি গ্রূপের vgg16 ডাটাসেট থেকে। এটা একটা প্রি-ট্রেইনড মডেল যা আসলে ‘ইমেজনেট’ নামে একটা বিশাল ডাটাসেট থেকে তৈরি করা। আমরা জানি যে ‘ইমেজনেট’ আসলে ১৪ লক্ষ ছবির একটা ডাটা সেট যার মধ্যে হাজারো ইন্টারনেটের ছবির ১০০০ ক্লাস বা ক্যাটেগরি আছে। এরমধ্যে কি ছবি নেই সেটাই অনেক চিন্তা করে বলতে হবে। আমরা যে ছবি প্রেডিক্ট করবো সেই ছবি ইমেজনেটে আছে কি নেই তার থেকে বড় ব্যাপার হচ্ছে ইমেজনেটকে ব্যবহার করছি ছবির বিভিন্ন ফিচার এক্সট্রাক্ট করার জন্য। ![](https://raw.githubusercontent.com/raqueeb/deep_learning_book/master/assets/vgg16.png) চিত্রঃ VGG-16 মডেল, ব্লক দিয়ে এখন আমাদেরকে চিন্তা করতে হবে প্রি-ট্রেইনড মডেল হিসেবে কোন লেয়ারটাকে ব্যবহার করব ফিচার এক্সট্রাকশন এর জন্য। অবশ্যই সবচেয়ে শেষের যে ক্লাসিফিকেশন লেয়ার \(সবচেয়ে শুরু’র, কারণ মেশিন লার্নিং মডেলগুলোর ডায়াগ্রাম শুরু হয় নিচ থেকে উপরে\) সেটা ফিচার এক্সট্রাকশন এর জন্য ভালো নয়। আমরা শেষের আগের লেয়ারটা ব্যবহার করি আগের লেয়ারের আউটপুটকে ‘ফ্ল্যাটেন’ করার জন্য। তার ঠিক আগের লেয়ার থেকে শুরু করে সবচেয়ে উপরের লেয়ার পর্যন্ত ফিচার এক্সট্রাক্ট করা যায়। ক্লাসিফায়ার লেয়ার এর আগেরটা ফ্ল্যাটেন লেয়ার। আর তার ঠিক আগের আগের লেয়ারটাই স্পেশালাইজড লেয়ার। উপর থেকে নিচ পর্যন্ত আস্তে আস্তে ফিচারগুলো কমপ্লেক্স হতে থাকে বলে শেষের দিকের লেয়ারগুলো স্পেশালাইজড লেয়ার। এই লেয়ারকে বলা হচ্ছে ‘বটলনেক’ লেয়ার। এখানে ‘বটলনেক’ ফিচারগুলো খুবই স্পেসিফিক একটা কাজের জন্য থাকে। আমরা একটা মডেলকে যখন ইনস্ট্যান্সিয়েট করব তখন include\_top=False আর্গুমেন্ট দিলেই ক্লাসিফিকেশন লেয়ার থাকবেনা শুরুতে। টপ লেয়ার ছাড়া একটা নেটওয়ার্ক লোড হবে। এটাই ফিচার ‘এক্সট্রাকশন’ এর জন্য সবচেয়ে ভালো অপশন। ![](https://raw.githubusercontent.com/raqueeb/deep_learning_book/master/assets/vgg-tune.png) চিত্রঃ VGG-16 মডেল, ফিচার এক্সট্র্যাক্টর অথবা ফাইন টিউনিং \`\`\`python \# মডেলের মাথা IMG\_SHAPE = \(IMAGE\_SIZE, IMAGE\_SIZE, 3\) vgg = tf.keras.applications.vgg16.VGG16\(weights='imagenet', include\_top=False, input\_shape=IMG\_SHAPE\) \`\`\` Downloading data from https://github.com/fchollet/deep-learning-models/releases/download/v0.1/vgg16\_weights\_tf\_dim\_ordering\_tf\_kernels\_notop.h5 58892288/58889256 \[==============================\] - 2s 0us/step \`\`\`python \# আগের মতো মডেলের শেষ অংশ যোগ করে দিচ্ছি দুটো বাড়তি লেয়ার average\_pool = tf.keras.layers.GlobalAveragePooling2D\(\) prediction = keras.layers.Dense\(1\) \`\`\` আমাদের vgg16 মডেলে ১৩টা কনভলিউশন লেয়ার আছে। এরমধ্যে ৩,৩ কনভলিউশন ফিল্টার এবং দরকারি ম্যাক্স পুলিং লেয়ার আছে ডাউন স্যাম্পলিং এর জন্য। এর মধ্যে দুটো ফুললি কানেক্টেড হিডেন লেয়ার যার ৪০৯৬ নোড ইউনিট আছে প্রতিটা লেয়ারে। এরপরে ১০০০ ইউনিটের ‘ডেন্স লেয়ার’ যা আসলে ১০০০ ক্যাটাগরির ছবির ক্লাসকে আইডেন্টিফাই করছে। আমাদের আসলে শেষের ৩ লেয়ার দরকার পড়ছে না, কারণ নিজেদের ফুললি কানেক্টেড ডেন্স লেয়ার ব্যবহার করব প্রেডিক্ট করতে - যে আসলে ছবিটা একটা কুকুরের না বিড়ালের? আমরা শুরুর পাঁচটা ব্লক নিয়ে ব্যস্ত থাকবো যেগুলো আসলে ফিচার এক্সট্রাকটর হিসেবে ব্যবহার হবে। ছবি দেখুন। আমাদের শুরুর মডেলে যেহেতু শুধুমাত্র ফিচার এক্সট্রাক্ট করব সে কারণে পাঁচটা কনভলিউশন ব্লককে ‘ফ্রিজ’ মানে ‘লক’ করে ফেলব যাতে তাদের ওয়েটগুলো আপডেট হতে না পারে প্রতিটা ইপকের পর। যেহেতু ট্রেনিং এর সময় লেয়ারগুলোর ‘ওয়েট’ দৈব-চয়নের ভিত্তিতে ইনিশিয়ালাইজ হয়, তাই সেই জিনিসটা ব্লকগুলোর আগের শেখা ওয়েটগুলো ভুলিয়ে দিতে পারে। ভুলিয়ে দিতে পারে বলছি ,এ কারণে আগের ট্রেনিংকৃত ফিচার ম্যাপগুলো উল্টাপাল্টা হয়ে যেতে পারে। সে কারণেই পাঁচটা ব্লক, মানে সব ব্লককেই ‘লক’ করে দিচ্ছি। \`\`\`python \# প্রি-ট্রেইনড মডেলের মাথা ট্রেইন করা যাবে না, একদম লক vgg.trainable = False \`\`\` \`\`\`python \# দেখি লেয়ারগুলোর অবস্থা, ট্রেইন করা যাবে না import pandas as pd pd.set\_option\('max\_colwidth', -1\) layer\_vgg = \[\(layer, layer.name, layer.trainable\) for layer in vgg.layers\] pd.DataFrame\(layer\_vgg, columns=\['Layer Type', 'Layer Name', 'Layer Trainable'\]\) \`\`\`  
    .dataframe tbody tr th:only-of-type {  
        vertical-align: middle;  
    }  
  
    .dataframe tbody tr th {  
        vertical-align: top;  
    }  
  
    .dataframe thead th {  
        text-align: right;  
    }  


|  | Layer Type | Layer Name | Layer Trainable |
| :--- | :--- | :--- | :--- |
| 0 | &lt;tensorflow.python.keras.engine.input\_layer.InputLayer object at 0x7f240242d710&gt; | input\_1 | False |
| 1 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24023cfc50&gt; | block1\_conv1 | False |
| 2 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f23efa09518&gt; | block1\_conv2 | False |
| 3 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f23ef9be7b8&gt; | block1\_pool | False |
| 4 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f23ef9be898&gt; | block2\_conv1 | False |
| 5 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f23ef9d0eb8&gt; | block2\_conv2 | False |
| 6 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f24014d8320&gt; | block2\_pool | False |
| 7 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014d8400&gt; | block3\_conv1 | False |
| 8 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014e3b70&gt; | block3\_conv2 | False |
| 9 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014f2e48&gt; | block3\_conv3 | False |
| 10 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f2401505fd0&gt; | block3\_pool | False |
| 11 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f2401497240&gt; | block4\_conv1 | False |
| 12 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014a79b0&gt; | block4\_conv2 | False |
| 13 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014b0c88&gt; | block4\_conv3 | False |
| 14 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f24014c4f60&gt; | block4\_pool | False |
| 15 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f2401455630&gt; | block5\_conv1 | False |
| 16 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014677f0&gt; | block5\_conv2 | False |
| 17 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f2401470ac8&gt; | block5\_conv3 | False |
| 18 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f2401483da0&gt; | block5\_pool | False |

```python
# ট্রেইন করার মতো ওয়েট আছে? না।

print("Trainable layers:", vgg.trainable_weights)
```

```text
Trainable layers: []
```

```python
# নতুন মডেল, প্রি-ট্রেইনড মডেল vgg16 সহ, tl_model মানে ট্রান্সফার লার্নিং মডেল (ইচ্ছেমতো নাম রাখুন)

tl_model = tf.keras.Sequential([
  vgg,
  average_pool,
  prediction,
  ])
```

```python
# সামারি দেখি

tl_model.summary()
```

```text
Model: "sequential_2"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
vgg16 (Model)                (None, 5, 5, 512)         14714688  
_________________________________________________________________
global_average_pooling2d_1 ( (None, 512)               0         
_________________________________________________________________
dense_1 (Dense)              (None, 1)                 513       
=================================================================
Total params: 14,715,201
Trainable params: 513
Non-trainable params: 14,714,688
_________________________________________________________________
```

```python
# মডেল কম্পাইল করছি

tl_model.compile(optimizer=tf.keras.optimizers.Adam(),
              loss='binary_crossentropy',
              metrics=['accuracy'])
```

```python
# টেন্সরবোর্ডের নতুন ডিরেক্টরি

callbacks = [tf.keras.callbacks.TensorBoard(log_dir='./log/transer_learning_model', update_freq='batch')]
```

```python
# মডেল ট্রেনিং, আবারো 
# ট্রান্সফার লার্নিং মডেলএর জন্য

# tl_model.fit(cat_train, steps_per_epoch = 23262//TRAIN_BATCH_SIZE, epochs=7, 
#             validation_data=cat_valid, validation_steps=10, callbacks=callbacks)

history = tl_model.fit(train_batches,
                    epochs=initial_epochs,
                    validation_data=validation_batches,
                    callbacks=callbacks)
```

```text
Epoch 1/10
582/582 [==============================] - 189s 325ms/step - loss: 0.3132 - accuracy: 0.8754 - val_loss: 0.0000e+00 - val_accuracy: 0.0000e+00
Epoch 2/10
582/582 [==============================] - 180s 309ms/step - loss: 1.0520 - accuracy: 0.8543 - val_loss: 0.4390 - val_accuracy: 0.8931
Epoch 3/10
582/582 [==============================] - 179s 308ms/step - loss: 0.3531 - accuracy: 0.9094 - val_loss: 0.2435 - val_accuracy: 0.9151
Epoch 4/10
582/582 [==============================] - 178s 306ms/step - loss: 0.2465 - accuracy: 0.9230 - val_loss: 0.2078 - val_accuracy: 0.9224
Epoch 5/10
582/582 [==============================] - 178s 306ms/step - loss: 0.2139 - accuracy: 0.9282 - val_loss: 0.2050 - val_accuracy: 0.9259
Epoch 6/10
582/582 [==============================] - 180s 309ms/step - loss: 0.2187 - accuracy: 0.9272 - val_loss: 0.1988 - val_accuracy: 0.9293
Epoch 7/10
582/582 [==============================] - 178s 306ms/step - loss: 0.1987 - accuracy: 0.9328 - val_loss: 0.1847 - val_accuracy: 0.9315
Epoch 8/10
582/582 [==============================] - 179s 308ms/step - loss: 0.3989 - accuracy: 0.9092 - val_loss: 0.2609 - val_accuracy: 0.9198
Epoch 9/10
582/582 [==============================] - 179s 308ms/step - loss: 0.2313 - accuracy: 0.9275 - val_loss: 0.2001 - val_accuracy: 0.9323
Epoch 10/10
582/582 [==============================] - 179s 307ms/step - loss: 0.3393 - accuracy: 0.9205 - val_loss: 0.9187 - val_accuracy: 0.8496
```

```python
# টেন্সরবোর্ড, নতুন পোর্টে

%tensorboard --logdir log/ --port=8008
```

  
  \(function\(\) {  
    window.TENSORBOARD\_ENV = window.TENSORBOARD\_ENV \|\| {};  
    window.TENSORBOARD\_ENV\["IN\_COLAB"\] = true;  
    document.querySelector\("base"\).href = "https://localhost:8008";  
    function fixUpTensorboard\(root\) {  
      const tftb = root.querySelector\("tf-tensorboard"\);  
      // Disable the fragment manipulation behavior in Colab. Not  
      // only is the behavior not useful \(as the iframe's location  
      // is not visible to the user\), it causes TensorBoard's usage  
      // of \`window.replace\` to navigate away from the page and to  
      // the \`localhost:&lt;port&gt;\` URL specified by the base URI, which  
      // in turn causes the frame to \(likely\) crash.  
      tftb.removeAttribute\("use-hash"\);  
    }  
    function executeAllScripts\(root\) {  
      // When \`script\` elements are inserted into the DOM by  
      // assigning to an element's \`innerHTML\`, the scripts are not  
      // executed. Thus, we manually re-insert these scripts so that  
      // TensorBoard can initialize itself.  
      for \(const script of root.querySelectorAll\("script"\)\) {  
        const newScript = document.createElement\("script"\);  
        newScript.type = script.type;  
        newScript.textContent = script.textContent;  
        root.appendChild\(newScript\);  
        script.remove\(\);  
      }  
    }  
    function setHeight\(root, height\) {  
      // We set the height dynamically after the TensorBoard UI has  
      // been initialized. This avoids an intermediate state in  
      // which the container plus the UI become taller than the  
      // final width and cause the Colab output frame to be  
      // permanently resized, eventually leading to an empty  
      // vertical gap below the TensorBoard UI. It's not clear  
      // exactly what causes this problematic intermediate state,  
      // but setting the height late seems to fix it.  
      root.style.height = \`${height}px\`;  
    }  
    const root = document.getElementById\("root"\);  
    fetch\("."\)  
      .then\(\(x\) =&gt; x.text\(\)\)  
      .then\(\(html\) =&gt; void \(root.innerHTML = html\)\)  
      .then\(\(\) =&gt; fixUpTensorboard\(root\)\)  
      .then\(\(\) =&gt; executeAllScripts\(root\)\)  
      .then\(\(\) =&gt; setHeight\(root, 800\)\);  
  }\)\(\);  
 \`\`\`python \# লম্বা টিউটোরিয়াল, একটু মডেল সেভ করে রাখি tl\_model.save\('cats\_dogs\_tlearn.h5'\) \`\`\` ২. প্রি-ট্রেইনড মডেলের ফাইন টিউনিং: পুরনো মডেলের কনভলিউশন বেইজের শুরুর দিকের লেয়ারগুলোকে ‘লক’ করে রেখে নিচের দিকের লেয়ারগুলোকে যদি ‘আনলক’ রাখি, তাহলে ক্লাসিফায়ার হেড এর ট্রেনিং এর সাথে সাথে আনলক লেয়ারগুলোর ট্রেনিং করানো সম্ভব। ফলে প্রি-ট্রেইনড মডেলের শেষের দিকের লেয়ারগুলোকে আমাদের কাজ অনুসারে দরকারি ফাইন টিউনিং করানো সম্ভব। এতে মডেল আমার স্পেসিফিক কাজের জন্য ভালোভাবে কাজ করবে। পরের অংশে আমরা যখন vgg16কে ফাইন টিউনিং করব, তখন ক্লাসিফায়ারের এর সাথে সাথে নিচের দুটো ব্লককে আনলক করে দেব। আমরা বলছি ব্লক ৪ এবং ৫ - যেগুলো আনলক করার ফলে তাদের ওয়েটগুলো আপডেট হবে প্রতি ইপকে, মডেল ট্রেনিং এর সাথে সাথে। নিচের ছবিটা একটু দেখি। এখানে কম্প্লেক্সিটি এড়ানোর জন্য আমরা ‘গ্লোবাল এভারেজ পুলিং’ আর যোগ করছিনা। কোডে সেটা দেখলে বুঝতে পারবেন। এই লেয়ারগুলোর ফিচার ম্যাপ থেকে যে আউটপুট পাব সেটাকে পাঠিয়ে দেব ‘ফ্ল্যাটেন’ লেয়ারে। এরপরের আউটপুট চলে যাবে আমাদের ক্লাসিফায়ারের ‘ডেন্স’ লেয়ারে। \`\`\`python \# এখন মডেলের ফাইন টিউনিং, ব্লক ৪ এবং ৫ 'আনলক' করে দিলাম tl\_model.trainable = True set\_trainable = False for layer in vgg.layers: if layer.name in \['block5\_conv1', 'block4\_conv1'\]: set\_trainable = True if set\_trainable: layer.trainable = True else: layer.trainable = False pd.set\_option\('max\_colwidth', -1\) layer\_vgg2 = \[\(layer, layer.name, layer.trainable\) for layer in vgg.layers\] pd.DataFrame\(layer\_vgg2, columns=\['Layer Type', 'Layer Name', 'Layer Trainable'\]\) \`\`\`  
    .dataframe tbody tr th:only-of-type {  
        vertical-align: middle;  
    }  
  
    .dataframe tbody tr th {  
        vertical-align: top;  
    }  
  
    .dataframe thead th {  
        text-align: right;  
    }  


|  | Layer Type | Layer Name | Layer Trainable |
| :--- | :--- | :--- | :--- |
| 0 | &lt;tensorflow.python.keras.engine.input\_layer.InputLayer object at 0x7f240242d710&gt; | input\_1 | False |
| 1 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24023cfc50&gt; | block1\_conv1 | False |
| 2 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f23efa09518&gt; | block1\_conv2 | False |
| 3 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f23ef9be7b8&gt; | block1\_pool | False |
| 4 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f23ef9be898&gt; | block2\_conv1 | False |
| 5 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f23ef9d0eb8&gt; | block2\_conv2 | False |
| 6 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f24014d8320&gt; | block2\_pool | False |
| 7 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014d8400&gt; | block3\_conv1 | False |
| 8 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014e3b70&gt; | block3\_conv2 | False |
| 9 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014f2e48&gt; | block3\_conv3 | False |
| 10 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f2401505fd0&gt; | block3\_pool | False |
| 11 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f2401497240&gt; | block4\_conv1 | True |
| 12 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014a79b0&gt; | block4\_conv2 | True |
| 13 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014b0c88&gt; | block4\_conv3 | True |
| 14 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f24014c4f60&gt; | block4\_pool | True |
| 15 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f2401455630&gt; | block5\_conv1 | True |
| 16 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f24014677f0&gt; | block5\_conv2 | True |
| 17 | &lt;tensorflow.python.keras.layers.convolutional.Conv2D object at 0x7f2401470ac8&gt; | block5\_conv3 | True |
| 18 | &lt;tensorflow.python.keras.layers.pooling.MaxPooling2D object at 0x7f2401483da0&gt; | block5\_pool | True |

```python
# মডেল কম্পাইল করছি

tl_model.compile(loss='binary_crossentropy',
              optimizer = tf.keras.optimizers.RMSprop(lr=base_learning_rate/10),
              metrics=['accuracy'])
```

```python
tl_model.summary()
```

```text
Model: "sequential_2"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
vgg16 (Model)                (None, 5, 5, 512)         14714688  
_________________________________________________________________
global_average_pooling2d_1 ( (None, 512)               0         
_________________________________________________________________
dense_1 (Dense)              (None, 1)                 513       
=================================================================
Total params: 14,715,201
Trainable params: 12,979,713
Non-trainable params: 1,735,488
_________________________________________________________________
```

```python
# টেন্সরবোর্ডের আবার নতুন ডিরেক্টরি

callbacks = [tf.keras.callbacks.TensorBoard(log_dir='./log/transer_learning_fine_tuning', update_freq='batch')]
```

```python
# মডেল ট্রেনিং, ফাইন টিউনিং এর জন্য

fine_tune_epochs = 10
total_epochs =  initial_epochs + fine_tune_epochs

fine_tuning = tl_model.fit(train_batches,
                         epochs=total_epochs,
                         initial_epoch = initial_epochs,
                         validation_data=validation_batches,
                         callbacks=callbacks)
```

```text
Epoch 11/20
      1/Unknown - 5s 5s/step - loss: 1.2135 - accuracy: 0.7812WARNING:tensorflow:Method (on_train_batch_end) is slow compared to the batch update (0.926102). Check your callbacks.


WARNING:tensorflow:Method (on_train_batch_end) is slow compared to the batch update (0.926102). Check your callbacks.


582/582 [==============================] - 251s 431ms/step - loss: 0.1919 - accuracy: 0.9518 - val_loss: 0.0000e+00 - val_accuracy: 0.0000e+00
Epoch 12/20
582/582 [==============================] - 241s 414ms/step - loss: 0.1190 - accuracy: 0.9748 - val_loss: 0.4140 - val_accuracy: 0.9375
Epoch 13/20
582/582 [==============================] - 242s 417ms/step - loss: 0.0777 - accuracy: 0.9854 - val_loss: 0.1355 - val_accuracy: 0.9776
Epoch 14/20
582/582 [==============================] - 242s 415ms/step - loss: 0.0526 - accuracy: 0.9916 - val_loss: 0.1369 - val_accuracy: 0.9767
Epoch 15/20
582/582 [==============================] - 241s 415ms/step - loss: 0.0409 - accuracy: 0.9941 - val_loss: 0.1532 - val_accuracy: 0.9746
Epoch 16/20
582/582 [==============================] - 243s 417ms/step - loss: 0.0362 - accuracy: 0.9954 - val_loss: 0.1592 - val_accuracy: 0.9759
Epoch 17/20
582/582 [==============================] - 242s 416ms/step - loss: 0.0367 - accuracy: 0.9962 - val_loss: 0.1789 - val_accuracy: 0.9716
Epoch 18/20
582/582 [==============================] - 243s 417ms/step - loss: 0.0340 - accuracy: 0.9962 - val_loss: 0.1441 - val_accuracy: 0.9780
Epoch 19/20
582/582 [==============================] - 242s 416ms/step - loss: 0.0259 - accuracy: 0.9973 - val_loss: 0.1897 - val_accuracy: 0.9754
Epoch 20/20
582/582 [==============================] - 243s 418ms/step - loss: 0.0266 - accuracy: 0.9973 - val_loss: 0.1324 - val_accuracy: 0.9772
```

```python
%tensorboard --logdir log/ --port=8009
```

![](https://raw.githubusercontent.com/raqueeb/deep_learning_book/master/assets/board2.PNG) ![](https://raw.githubusercontent.com/raqueeb/deep_learning_book/master/assets/board3.PNG)

