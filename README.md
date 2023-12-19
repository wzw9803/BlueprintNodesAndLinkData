# BlueprintNodesAndLinkData

## LinkData
```
{
	'documents': [{
		'name': '蓝图1',
		'pages': [{
			'name': '页-1',
			'comments': [{
				'width': 230.95995687330796,
				'height': 160.2,
				'position': [
					'190',
					'-64'
				],
				'title': '注释',
				'nodes': [
					4
				]
			}],
			'nodes': [{
				'name': 'Begin',
				'position': [
					'-320',
					'-63.99999999999999'
				],
				'data': {},
				'inputs': {},
				'outputs': {
					'start': {}
				},
				'title': '开始'
			},
			{
				'name': 'macro1',
				'position': [
					'-69.49999999999999',
					'-63.99999999999999'
				],
				'data': {},
				'inputs': {
					'input1': {}
				},
				'outputs': {
					'output1': {}
				},
				'title': '宏_1',
				'type': 'macro',
				'macro': 0
			},
			{
				'name': 'Begin',
				'title': '开始',
				'position': [
					'-373.86001078167305',
					'-339.5'
				],
				'data': {},
				'inputs': {},
				'outputs': {
					'start': {}
				},
				'hidden': true
			},
			{
				'name': 'Switch',
				'position': [
					'-60.654001874153955',
					'-332'
				],
				'data': {},
				'inputs': {
					'exec': {
						'folded': true
					},
					'value': {}
				},
				'outputs': {},
				'title': 'Switch'
			},
			{
				'name': 'Print',
				'position': [
					'190',
					'-64'
				],
				'data': {
					'type': 'debug'
				},
				'inputs': {
					'exec': {},
					'value': {
						'value': '蓝图页打印1'
					}
				},
				'outputs': {
					'next': {}
				},
				'title': '打印'
			}
			],
			'connections': [{
				'from': {
					'node': 1,
					'output': 'start'
				},
				'to': {
					'node': 2,
					'input': 'input1'
				}
			},
			{
				'from': {
					'node': 2,
					'output': 'output1'
				},
				'to': {
					'node': 4,
					'input': 'exec'
				}
			},
			{
				'from': {
					'node': 4,
					'output': 'start'
				},
				'to': {
					'node': 3,
					'input': 'exec'
				}
			}
			]
		}]
	}],
	'macros': [
		{
			'name': '宏_1',
			'inputs': [{
				'title': 'input1',
				'name': 'input1',
				'type': 'exec'
			}],
			'outputs': [{
				'name': 'output1',
				'title': 'output1',
				'type': 'exec'
			}],
			'pages': [{
				'name': '页-1',
				'comments': [],
				'nodes': [{
					'name': 'macro1_$virtual_input',
					'position': [
						'-562.5',
						'-368.5'
					],
					'data': {},
					'inputs': {},
					'outputs': {
						'input1': {}
					},
					'title': '输入'
				},
				{
					'name': 'macro1_$virtual_output',
					'position': [
						'137.5',
						'-368.5'
					],
					'data': {},
					'inputs': {
						'output1': {}
					},
					'outputs': {},
					'title': '输出'
				},
				{
					'name': 'Print',
					'position': [
						'-339',
						'-368.5'
					],
					'data': {
						'type': 'debug'
					},
					'inputs': {
						'exec': {},
						'value': {
							'value': '宏1打印'
						}
					},
					'outputs': {
						'next': {}
					},
					'title': '打印'
				}
				],
				'connections': [{
					'from': {
						'node': 1,
						'output': 'input1'
					},
					'to': {
						'node': 0,
						'input': 'exec'
					}
				},
				{
					'from': {
						'node': 1,
						'output': 'next'
					},
					'to': {
						'node': 2,
						'input': 'output1'
					}
				}
				],
			}],

		}
	],
	'collapses': [],
	'states': [],
	'version': '4'
}
```
documents：一个包含一个蓝图文件的数组。
  name：蓝图的名称。
  pages：蓝图的页面数组，每个页面代表了一个流程图的具体步骤。
    name：页面的名称。
    comments：页面的注释数组，每个注释代表了一个说明性的标记。
    nodes：节点数组，每个节点代表了一个操作组件。
      name：节点的名称。
      position：节点在页面上的位置坐标。
      data：节点的数据。
      inputs：节点的输入属性。
      outputs：节点的输出属性。
      title：节点的标题。
      type：节点的类型。目前只有 macro collapse state 或者 undefined(默认)
      macro: 宏的索引。根据type的类型，会有对应的字段如：macro: 1 或 collapse: 0 或 state：0
    connections：连接数组，每个连接代表了两个节点之间的数据传递关系。
      from：连接的起始节点。
        node：节点的唯一标识符。
        output：节点的输出属性名称。
      to：连接的终止节点。
        node：节点的唯一标识符。
        input：节点的输入属性名称。
macros：一个包含可重用的宏对象的数组。可以一个节点的形式在图中使用。
  inputs：宏的输入属性数组。
  outputs：宏的输出属性数组。
  其余和blueprint完全一致
collapses：折叠对象数组。数据格式和宏一致，只不过不提供复用功能。
states：状态子图数组。其数据格式和blueprints完全一致
version：JSON 数据格式的版本号。
