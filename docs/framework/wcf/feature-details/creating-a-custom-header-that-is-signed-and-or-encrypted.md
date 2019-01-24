---
title: Tworzenie niestandardowego nagłówka, który jest podpisany i- lub zaszyfrowany
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 0f8f86bcb5494cd502d14aff1cf3c4cdf4f8dd33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494824"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Tworzenie niestandardowego nagłówka, który jest podpisany i- lub zaszyfrowany
Podczas wywoływania usługi WCF nie przy użyciu klienta programu WCF czasami jest niezbędne do korzystania z niestandardowych nagłówków protokołu SOAP. W programie WCF, który uniemożliwia Nagłówki niestandardowe, które są podpisane i szyfrowane pracy z usługą WCF nie znajduje się błąd kanoniczną. Przyczyną problemu jest niepoprawna canonicalization domyślnych XML w przestrzeni nazw. Jest to tylko problemy podczas wywoływania usług innych niż WCF za pomocą Nagłówki niestandardowe, które są podpisane i/lub zaszyfrowanego.  Gdy usługa odbiera komunikat zawierający podpisanego i/lub zaszyfrowanego niestandardowego nagłówka nie może zweryfikować podpisu. To rozwiązanie pozwala uniknąć błędów canonicalization, umożliwia współdziałanie z usługami innych WCF, ale nie uniemożliwia współdziałanie z usługami WCF.  
  
## <a name="defining-the-custom-header"></a>Definiowanie niestandardowego nagłówka  
 Niestandardowe nagłówki są definiowane przez definiowanie kontraktu komunikatu i oznaczanie elementów członkowskich mają być wysyłane jako nagłówków z <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu. Aby obejść ten błąd canonicalization musi zapewnić, że serializator XML deklaruje przestrzeń nazw dla niestandardowego nagłówka z prefiksem zamiast deklarację domyślnej przestrzeni nazw. Poniższy kod pokazuje jak zdefiniować typ danych, która będzie służyć jako nagłówek komunikatu z deklaracją poprawną przestrzeń nazw.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 Ten kod deklaruje nowy typ o nazwie `msgHeaderElement` będą wykonywane szeregowo przy użyciu elementu Serializującego XML. W przypadku wystąpienia tego typu jest serializowana, określi przestrzeni nazw z prefiksem "h", ten sposób obejść usterki kanoniczną.  Kontraktu komunikatu, następnie należy zdefiniować wystąpienie `msgHeaderElement` i oznacz go za pomocą <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu, jak pokazano w poniższym przykładzie.  
  
```  
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a>Zobacz także
- [Domyślny kontrakt komunikatów](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [Kontrakty komunikatów](../../../../docs/framework/wcf/samples/message-contracts.md)
- [Używanie kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
