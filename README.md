vim-react-es6-snippets
==================

A set of snippets for Vim to work with Facebook's [React](http://facebook.github.io/react/) library.

A direct port of the awesome snippets from 
[justinj/vim-react-snippets](https://github.com/justinj/vim-react-snippets).

Requires [vim-snipmate](https://github.com/garbas/vim-snipmate).

Installation
============

Use your preferred Vim plugin installation method.  Vundle or Pathogen should be fine (I use Pathogen).

Usage
=====

```Javscript
snippet rsc "React Hooks Function" b
import React from 'react'
import { string, $5 } from 'prop-types'
import { Container, $4 } from './$1.styles'

export default function ${1:`!v expand('%:t:r')`}({$3}) {
	return (
		<Container>
			$4
		</Container>
	)
}

$1.propTypes = {
}
endsnippet

snippet rnsiov "React Native Create Story(iOv project)" b
import React from 'react'
import ${1:`!v expand('%:t:r')`} from './$1'
import { storiesOf } from '@storybook/react-native'
import { withKnobs } from '@storybook/addon-knobs'

import { RNETheme, stackNavigationDecorator } from '~/storybook/decorators'
import { mockProps } from './$1.mock'

storiesOf('$1', module)
	.addDecorator(stackNavigationDecorator)
	.addDecorator(RNETheme)
	.addDecorator(withKnobs)
	.add('default', () => <$1 {...mockProps} />)
endsnippet

snippet rnspciov "React Native Spec file (iOv project)" b
import React from 'react'
import ${1:`!v expand('%:t:r')`} from './$1'
import { mockProps } from './$1.mock'

import { render } from '~/jest'

it('renders correctly', () => {
	const wrapper = render(<$1 {...mockProps} />)
	expect(wrapper.toJSON()).toMatchSnapshot()
})
endsnippet

snippet rnsciov "React Native styled component(iOv project)" b
import styled from 'styled-components/native'
import theme from '~/app/styles'

export const Container = styled.View\`\`
endsnippet

snippet rnmockiov "React Native mock (iOv project)" b
import React from 'react'
import { Back${1:, Close} } from '~/app/components/base'

export const mockProps = {
	headerTitle: '$2',
	headerLeft: <Back />,
	${1:headerRight: <Close />,}
	placeName: 'Dunedin Bush Camp and Lodge Long Name',
}
endsnippet

snippet ue "React useEffect" b
useEffect(() => {
}, $1)
endsnippet

snippet immh "Import hooks" b
import React, { useState${2:, useEffect} } from 'react'
endsnippet

snippet us "React useEffect" b
const [$1, set$2] = useState($3)
endsnippet

snippet rrcc "React Redux Class Component" b
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { connect } from 'react-redux'
import { bindActionCreators } from 'redux'
import * as $2ActionCreators from '../../redux/modules/$2'

class ${1:`!v expand('%:t:r')`} extends Component {
	static propTypes = {
		children: PropTypes.node,
		dispatch: PropTypes.func.isRequired,
	}

	render() {
		return (
			${3:null}
		)
	}
}

function mapStateToProps (state) {
	return {}
}

function mapDispatchToProps (dispatch) {
	return bindActionCreators($2ActionCreators, dispatch)
}

export default connect(mapStateToProps, mapDispatchToProps)($1)
endsnippet

snippet rrncc "create redux native class/component" b
import React, { Component } from 'react'
import PropTypes from 'prop-types'
import { View } from 'react-native'
import { connect } from 'react-redux'
import { bindActionCreators } from 'redux'

import * as $2ActionCreators from '../../redux/modules/$2'

class ${1:`!v expand('%:t:r')`} extends Component {
	static propTypes = {
		children: PropTypes.node,
	}

	render () {
		return (
			<View>$0</View>
		)
	}
}

function mapStateToProps ({$2}) {
	return {$2}
}

function mapDispatchToProps (dispatch) {
	return bindActionCreators($2ActionCreators, dispatch)
}

export default connect(mapStateToProps, mapDispatchToProps)($1)
endsnippet


snippet rncsc "create native stateless component" b
import React from 'react'
import { View, Text, ${3:StyleSheet} } from 'react-native'

export default function ${1:`!v expand('%:t:r')`}(props) {
	return (
		<View>
			<Text>$2</Text>
		</View>
	)
}

${3:const styles = StyleSheet.create({
})}
endsnippet

snippet im "import" b
import $1 from '$2'
endsnippet

snippet imm "import with brackets" b
import { $1 } from '$2'
endsnippet

snippet ex "export component" b
export { default as $1$2 } from './$1/$1$2'
endsnippet

snippet fu "create function" i
function $1($2) {
	$3
}
endsnippet

snippet ef "export function" b
export function $1($2) {
	$3
}
endsnippet

snippet edf "export default function" b
export default function $1($2) {
	${3}
}
endsnippet

snippet () "annon function" i
() => ${1:{}}
endsnippet

snippet if "if statement"
if ($1){
	$2
}
endsnippet

snippet dp "default props" b
$1.defaultProps = {
	$2: $3,
}
endsnippet

snippet pt "propTypes" b
$1.propTypes = {
	$2: ${3:string}.isRequired,
}
endsnippet

snippet ptp "propType partial" b
	$1: ${2:string}${3:.isRequired},
endsnippet

snippet cs "create StyleSheet" b
const styles = StyleSheet.create({
	$1: {
		$2: $3,
	},
})
endsnippet

snippet cl "log console" i
console.log($1)
endsnippet

snippet ce "log error console" i
console.error($1)
endsnippet

snippet co "const" i
const $1 = $2
endsnippet

snippet le "let" i
let $1 = $2
endsnippet

snippet db "debugger" b
debugger
endsnippet

snippet rr "redux reducer" i
const initialState = {}

export default function ${1:`!v expand('%:t:r')`} (state = initialState, action) {
	switch (action.type) {

		default :
			return state
	}
}
endsnippet

snippet rcs "redux case switch" b
case $1 :
	return { ...state, ...{$2: action.$2} }
endsnippet

snippet rce "redux case switch" b
case $1_ERROR :
	return {
		...state,
		action.errors
	}
endsnippet

snippet racc "redux action creator with constant" b
export const $3 = '$3'
export function $1 ($2) {
	return {
		type: $3,$0
	}
}
endsnippet

snippet rac "redux action creator" b
export function ${1} (${2}) {
	return {
		type: ${3},$0
	}
}
endsnippet

snippet try "try/catch block" b
try {

} catch (error) {
	console.error(error)
}
endsnippet
```
