---
title: Tworzenie podpisanego i/lub zaszyfrowanego niestandardowego nagłówka
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 76bfb6040f6b78765ed42ce7fbf86cdbd62c1e48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075650"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="3db9c-102">Tworzenie podpisanego i/lub zaszyfrowanego niestandardowego nagłówka</span><span class="sxs-lookup"><span data-stu-id="3db9c-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="3db9c-103">Podczas wywoływania usługi WCF nie przy użyciu klienta programu WCF czasami jest niezbędne do korzystania z niestandardowych nagłówków protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3db9c-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="3db9c-104">W programie WCF, który uniemożliwia Nagłówki niestandardowe, które są podpisane i szyfrowane pracy z usługą WCF nie znajduje się błąd kanoniczną.</span><span class="sxs-lookup"><span data-stu-id="3db9c-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="3db9c-105">Przyczyną problemu jest niepoprawna canonicalization domyślnych XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3db9c-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="3db9c-106">Jest to tylko problemy podczas wywoływania usług innych niż WCF za pomocą Nagłówki niestandardowe, które są podpisane i/lub zaszyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="3db9c-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="3db9c-107">Gdy usługa odbiera komunikat zawierający podpisanego i/lub zaszyfrowanego niestandardowego nagłówka nie może zweryfikować podpisu.</span><span class="sxs-lookup"><span data-stu-id="3db9c-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="3db9c-108">To rozwiązanie pozwala uniknąć błędów canonicalization, umożliwia współdziałanie z usługami innych WCF, ale nie uniemożliwia współdziałanie z usługami WCF.</span><span class="sxs-lookup"><span data-stu-id="3db9c-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="3db9c-109">Definiowanie niestandardowego nagłówka</span><span class="sxs-lookup"><span data-stu-id="3db9c-109">Defining the custom header</span></span>  
 <span data-ttu-id="3db9c-110">Niestandardowe nagłówki są definiowane przez definiowanie kontraktu komunikatu i oznaczanie elementów członkowskich mają być wysyłane jako nagłówków z <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3db9c-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="3db9c-111">Aby obejść ten błąd canonicalization musi zapewnić, że serializator XML deklaruje przestrzeń nazw dla niestandardowego nagłówka z prefiksem zamiast deklarację domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3db9c-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="3db9c-112">Poniższy kod pokazuje jak zdefiniować typ danych, która będzie służyć jako nagłówek komunikatu z deklaracją poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="3db9c-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="3db9c-113">Ten kod deklaruje nowy typ o nazwie `msgHeaderElement` będą wykonywane szeregowo przy użyciu elementu Serializującego XML.</span><span class="sxs-lookup"><span data-stu-id="3db9c-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="3db9c-114">W przypadku wystąpienia tego typu jest serializowana, określi przestrzeni nazw z prefiksem "h", ten sposób obejść usterki kanoniczną.</span><span class="sxs-lookup"><span data-stu-id="3db9c-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="3db9c-115">Kontraktu komunikatu, następnie należy zdefiniować wystąpienie `msgHeaderElement` i oznacz go za pomocą <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3db9c-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3db9c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3db9c-116">See also</span></span>

- [<span data-ttu-id="3db9c-117">Domyślny kontrakt komunikatów</span><span class="sxs-lookup"><span data-stu-id="3db9c-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [<span data-ttu-id="3db9c-118">Kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="3db9c-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)
- [<span data-ttu-id="3db9c-119">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="3db9c-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
