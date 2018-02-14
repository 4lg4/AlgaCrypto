
import crypto from 'crypto'
import defaults from './env-config.json'

export default class AlgaCrypto {
    constructor(props = {}) {
        if(typeof props === "string"){
            this.props = defaults;
            this.props.toEncrypt = props;
            this.encrypt();
            return this;
        }

        this.props = Object.assign(defaults, props);
    }


    encrypt(text){
        const cipher = crypto.createCipher(this.props.algorithm,this.props.password);
        let crypted = cipher.update(text || this.props.toEncrypt,'utf8','hex');
        crypted += cipher.final('hex');
        this.props.encrypted = crypted;
        return crypted;
    }


    decrypt(text){
        const decipher = crypto.createDecipher(this.props.algorithm,this.props.password);
        let dec = decipher.update(text || this.props.encrypted,'hex','utf8');
        dec += decipher.final('utf8');
        return dec;
    }

}
