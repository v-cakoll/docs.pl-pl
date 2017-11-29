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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ac43be1978a2a6e80b08e0c4bcd5e0e92043719e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="88b78-102">Tworzenie niestandardowego nagłówka, który jest podpisany i- lub zaszyfrowany</span><span class="sxs-lookup"><span data-stu-id="88b78-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="88b78-103">Podczas wywoływania usługi WCF z systemem innym niż przy użyciu klienta programu WCF czasami jest konieczne użycie niestandardowe nagłówki SOAP.</span><span class="sxs-lookup"><span data-stu-id="88b78-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="88b78-104">W programie WCF, która uniemożliwia niestandardowe nagłówki, które są podpisane i zaszyfrowane pracy z usługą WCF z systemem innym niż Brak usterki zapewniania kanoniczności.</span><span class="sxs-lookup"><span data-stu-id="88b78-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="88b78-105">Przyczyną problemu jest nieprawidłowego rozpoznawania zgodności domyślne obszary nazw XML.</span><span class="sxs-lookup"><span data-stu-id="88b78-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="88b78-106">Jest to tylko powodować problemy podczas wywoływania usługi WCF z systemem innym niż z niestandardowe nagłówki, które są podpisane i/lub szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="88b78-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="88b78-107">Gdy usługa odbiera komunikat zawierający podpisanego i/lub zaszyfrowanego niestandardowego nagłówka nie może zweryfikować podpisu.</span><span class="sxs-lookup"><span data-stu-id="88b78-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="88b78-108">To rozwiązanie pozwala uniknąć błędów zapewniania kanoniczności, umożliwia współdziałanie z usługami innych niż WCF, ale nie zapobiega współdziałanie z usługami WCF.</span><span class="sxs-lookup"><span data-stu-id="88b78-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="88b78-109">Definiowanie niestandardowego nagłówka</span><span class="sxs-lookup"><span data-stu-id="88b78-109">Defining the custom header</span></span>  
 <span data-ttu-id="88b78-110">Nagłówki niestandardowe są definiowane przez definiowanie kontraktu komunikatu i oznaczanie elementów członkowskich mają być wysyłane jako nagłówków z <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="88b78-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="88b78-111">Aby obejść usterki zapewniania kanoniczności musi upewnij się, że serializatora XML deklaruje przestrzeni nazw z prefiksem zamiast deklarację domyślnej przestrzeni nazw niestandardowego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="88b78-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="88b78-112">Poniższy kod przedstawia sposób definiowania typu danych, który będzie używany jako nagłówek wiadomości z deklaracją poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="88b78-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="88b78-113">Ten kod deklaruje nowy typ o nazwie `msgHeaderElement` będą wykonywane szeregowo z serializatora XML.</span><span class="sxs-lookup"><span data-stu-id="88b78-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="88b78-114">W przypadku wystąpienia tego typu jest serializowana, określi przestrzeni nazw z prefiksem "h", w związku z tym pracy wokół usterki zapewniania kanoniczności.</span><span class="sxs-lookup"><span data-stu-id="88b78-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="88b78-115">Kontraktu komunikatu może następnie zdefiniować wystąpienia `msgHeaderElement` i oznacz ją z <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="88b78-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88b78-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88b78-116">See Also</span></span>  
 [<span data-ttu-id="88b78-117">Domyślny kontrakt komunikatów</span><span class="sxs-lookup"><span data-stu-id="88b78-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [<span data-ttu-id="88b78-118">Kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="88b78-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [<span data-ttu-id="88b78-119">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="88b78-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
