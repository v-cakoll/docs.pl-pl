---
title: "Tworzenie niestandardowego nagłówka, który jest podpisany i- lub zaszyfrowany"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b0faa62d75c506fd93c17c6a67aaecdd22bc8c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Tworzenie niestandardowego nagłówka, który jest podpisany i- lub zaszyfrowany
Podczas wywoływania usługi WCF z systemem innym niż przy użyciu klienta programu WCF czasami jest konieczne użycie niestandardowe nagłówki SOAP. W programie WCF, która uniemożliwia niestandardowe nagłówki, które są podpisane i zaszyfrowane pracy z usługą WCF z systemem innym niż Brak usterki zapewniania kanoniczności. Przyczyną problemu jest nieprawidłowego rozpoznawania zgodności domyślne obszary nazw XML. Jest to tylko powodować problemy podczas wywoływania usługi WCF z systemem innym niż z niestandardowe nagłówki, które są podpisane i/lub szyfrowane.  Gdy usługa odbiera komunikat zawierający podpisanego i/lub zaszyfrowanego niestandardowego nagłówka nie może zweryfikować podpisu. To rozwiązanie pozwala uniknąć błędów zapewniania kanoniczności, umożliwia współdziałanie z usługami innych niż WCF, ale nie zapobiega współdziałanie z usługami WCF.  
  
## <a name="defining-the-custom-header"></a>Definiowanie niestandardowego nagłówka  
 Nagłówki niestandardowe są definiowane przez definiowanie kontraktu komunikatu i oznaczanie elementów członkowskich mają być wysyłane jako nagłówków z <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu. Aby obejść usterki zapewniania kanoniczności musi upewnij się, że serializatora XML deklaruje przestrzeni nazw z prefiksem zamiast deklarację domyślnej przestrzeni nazw niestandardowego nagłówka. Poniższy kod przedstawia sposób definiowania typu danych, który będzie używany jako nagłówek wiadomości z deklaracją poprawną przestrzeń nazw.  
  
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
  
 Ten kod deklaruje nowy typ o nazwie `msgHeaderElement` będą wykonywane szeregowo z serializatora XML. W przypadku wystąpienia tego typu jest serializowana, określi przestrzeni nazw z prefiksem "h", w związku z tym pracy wokół usterki zapewniania kanoniczności.  Kontraktu komunikatu może następnie zdefiniować wystąpienia `msgHeaderElement` i oznacz ją z <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Domyślny kontrakt komunikatów](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [Kontrakty komunikatów](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [Używanie kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
