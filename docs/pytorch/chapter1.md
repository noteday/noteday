## pack_padded_sequence
>torch.nn.utils.rnn.pack_padded_sequence(input, lengths,batch_first=False, enforce_sorted=True)  

**Packs a Tensor containing padded sequences of variable length.**

**input** can be of size **T x B x *** where T is the length of the longest sequence (equal to lengths[0]), B is the batch size, and * is any number of dimensions (including 0). If batch_first is True, B x T x * input is expected.

For unsorted sequences, use enforce_sorted = False. If enforce_sorted is True, the sequences should be sorted by length in a decreasing order, i.e. input[:,0] should be the longest sequence, and input[:,B-1] the shortest one. enforce_sorted = True is only necessary for ONNX export.

>Parameters

+ **input** (Tensor) – padded batch of variable length sequences.
+ **lengths** (Tensor) – list of sequences lengths of each batch element.
+ **batch_first** (bool, optional) – if True, the input is expected in B x T x * format.
+ **enforce_sorted** (bool, optional) – if True, the input is expected to contain sequences sorted by length in a decreasing order. If False, the input will get sorted unconditionally. Default: True.

## torch.argsort
>torch.argsort(input, dim=-1, descending=False ) → LongTensor 

**Returns the indices that sort a tensor along a given dimension in ascending order by value.**


>Parameters

+ **input** (Tensor) – the input tensor.
+ **dim** (int, optional) – the dimension to sort along
+ **descending** (bool, optional) – controls the sorting order (ascending or descending)

>Example:

```python
>>> a = torch.randn(4, 4)
>>> a
tensor([[ 0.0785,  1.5267, -0.8521,  0.4065],
        [ 0.1598,  0.0788, -0.0745, -1.2700],
        [ 1.2208,  1.0722, -0.7064,  1.2564],
        [ 0.0669, -0.2318, -0.8229, -0.9280]])


>>> torch.argsort(a, dim=1)
tensor([[2, 0, 3, 1],
        [3, 2, 1, 0],
        [2, 1, 0, 3],
        [3, 2, 1, 0]])
```


## LSTM
>CLASStorch.nn.LSTM(*args, **kwargs)

**[LSTM详情](nlp/chapter1.md)**


>Parameters

+ **input_size** – The number of expected features in the input x
+ **hidden_size** – The number of features in the hidden state h
+ **num_layers** – Number of recurrent layers. E.g., setting num_layers=2 would mean stacking two LSTMs together to form a stacked LSTM, with the second LSTM taking in outputs of the first LSTM and computing the final results. Default: 1
+ **bias** – If False, then the layer does not use bias weights b_ih and b_hh. Default: True
+ **batch_first** – If True, then the input and output tensors are provided as (batch, seq, feature). Default: False
+ **dropout** – If non-zero, introduces a Dropout layer on the outputs of each LSTM layer except the last layer, with dropout probability equal to dropout. Default: 0
+ **bidirectional** – If True, becomes a bidirectional LSTM. Default: False

>Inputs: input, (h_0, c_0)

+ **input of shape (seq_len, batch, input_size)**: tensor containing the features of the input sequence. The input can also be a packed variable length sequence. See torch.nn.utils.rnn.pack_padded_sequence() or torch.nn.utils.rnn.pack_sequence() for details.
+ **h_0 of shape (num_layers * num_directions, batch, hidden_size)**: tensor containing the initial hidden state for each element in the batch. If the LSTM is bidirectional, num_directions should be 2, else it should be 1.
+ **c_0 of shape (num_layers * num_directions, batch, hidden_size)**: tensor containing the initial cell state for each element in the batch.

If (h_0, c_0) is not provided, both h_0 and c_0 default to zero.

> Outputs: output, (h_n, c_n)

+ **output of shape (seq_len, batch, num_directions * hidden_size)**: tensor containing the output features (h_t) from the last layer of the LSTM, for each t. If a torch.nn.utils.rnn.PackedSequence has been given as the input, the output will also be a packed sequence.

For the unpacked case, the directions can be separated using output.view(seq_len, batch, num_directions, hidden_size), with forward and backward being direction 0 and 1 respectively. Similarly, the directions can be separated in the packed case.

+ **h_n of shape (num_layers * num_directions, batch, hidden_size)**: tensor containing the hidden state for t = seq_len.

Like output, the layers can be separated using h_n.view(num_layers, num_directions, batch, hidden_size) and similarly for c_n.

+ **c_n of shape (num_layers * num_directions, batch, hidden_size)**: tensor containing the cell state for t = seq_len.
