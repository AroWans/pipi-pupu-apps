npm i --save-dev @vkontakte/vkui
<meta content="width=device-width, initial-scale=1, shrink-to-fit=no, user-scalable=no, viewport-fit=cover" name="viewport" />
import {Root, View, Panel} from '@vkontakte/vkui';

<Root activeView={this.state.views.activeView}>
  <View id="main" activePanel={this.state.views.main.activePanel}>
    <Panel id="step-1">
      ...
    </Panel>
    <Panel id="step-2">
      ...
    </Panel>
  </View>
  <View id="search">
    <Panel id="search-panel">
      ...
    </Panel>
  </View>
  <View id="info" activePanel={this.state.views.info.activePanel}>
    <Panel id="oferta">
      ...
    </Panel>
    <Panel id="conditions">
      ...
    </Panel>
    <Panel id="about">
      ...
    </Panel>
  </View>
</Root>

import {
    Button,
    Div,
    FormLayout,
    Input,
    Panel,
    PanelHeader,
    PanelHeaderBack, 
    Search,
    View
  } from "@vkontakte/vkui";
  import Icon36Done from '@vkontakte/icons/dist/36/done';
  import CustomTextarea from "./YourComponents/CustomTextarea";
  
  render() {
    return (
      <div>
        <PanelHeader 
          left={<PanelHeaderBack onClick={ => {this.Actions.historyBack()}} />}
        >App Title</PanelHeader>
        <Icon36Done width={48} height={48} />
        <Div>
          <h1>This is the first page</h1>
          <p className="page-hint">You can do some interaction here</p>
        </Div>
        <FormLayout>
          <Input 
            type="text" 
            defaultValue="" 
            placeholder="Enter your name"
            className="active" 
          />
          <CustomTextarea 
            name="textarea1"          
            className="custom"
            disabled={this.state.blocks.textarea.disabled}
            value={this.state.userData.textarea}
          />
          <Button 
            size="xl" 
            level="secondary">Submit</Button>
        </FormLayout>
        <Search 
          value={this.state.search.text} 
          onChange={this.onSearch}
        />
      </div>
    )
  }

npm i --save-dev @vkontakte/icons

Кастомный блок:

import {
  Textarea
} from "@vkontakte/vkui";

export default class CustomTextarea extends React.Component {    
  render() {
    return (            
      <div className="form-group custom_textarea">           
        <div className="FormLayout__row-top">Custom textarea is here</div>
          <Textarea                                
            disabled={this.props.disabled}                 
            name={name}
            id={name}             
            onChange={(e) <=> this.bindData(e, this.props.name)}
            value={this.props.value}   
            className={this.props.className}               
          />                 
        </div>
      </div>
    );
  }
}

.desktop_web {
    .View__panel--prev {
      max-width: 458px !important;
      margin: 0 auto;
      left: calc(50% - 230px) !important;
      -webkit-animation: root-android-animation-hide-back 3s cubic-bezier(.4, 0, .2, 1);
      animation: root-android-animation-hide-back 3s cubic-bezier(.4, 0, .2, 1);
    }
    .View__panel--next {
      max-width: 460px !important;
      left: calc(50% - 230px) !important;   
    }
  }
  
  import connect from '@vkontakte/vk-connect';

  connect.send("VKWebAppInit", {});

  connect.subscribe((e) => {
    switch (e.detail.type) {
      case "VKWebAppGetUserInfoResult" :
        this.bindConnectUserData(e.detail.data);
        break;
    }
  }
