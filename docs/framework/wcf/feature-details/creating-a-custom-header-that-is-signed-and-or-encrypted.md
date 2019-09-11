---
title: Tworzenie podpisanego i/lub zaszyfrowanego niestandardowego nagłówka
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: d737647f8c0442a3d6fa0d077a1ffe2c251ea043
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856177"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a><span data-ttu-id="c794e-102">Tworzenie podpisanego i/lub zaszyfrowanego niestandardowego nagłówka</span><span class="sxs-lookup"><span data-stu-id="c794e-102">Creating a custom header that is signed and-or encrypted</span></span>
<span data-ttu-id="c794e-103">Podczas wywoływania usługi niezwiązanej z usługą WCF przy użyciu klienta WCF czasami konieczne jest użycie niestandardowych nagłówków protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c794e-103">When calling a non-WCF service using a WCF client it is sometimes necessary to use custom SOAP headers.</span></span> <span data-ttu-id="c794e-104">W programie WCF występuje błąd kanonizacji, który uniemożliwia tworzenie niestandardowych nagłówków podpisanych i szyfrowanych podczas pracy z usługą nieobsługującą usług WCF.</span><span class="sxs-lookup"><span data-stu-id="c794e-104">There is a canonicalization bug in WCF that prevents custom headers that are signed and encrypted from working with a non-WCF service.</span></span> <span data-ttu-id="c794e-105">Problem jest spowodowany niepoprawnym kanonizacją domyślnych przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="c794e-105">The problem is caused by the incorrect canonicalization of default XML namespaces.</span></span> <span data-ttu-id="c794e-106">Jest to problematyczne tylko podczas wywoływania usług innych niż usługi WCF z niestandardowymi nagłówkami, które są podpisane i/lub szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="c794e-106">This is only problematic when calling non-WCF services with custom headers that are signed and/or encrypted.</span></span>  <span data-ttu-id="c794e-107">Gdy usługa otrzymuje komunikat zawierający podpisany i/lub zaszyfrowany nagłówek niestandardowy, nie można zweryfikować podpisu.</span><span class="sxs-lookup"><span data-stu-id="c794e-107">When the service receives the message containing the signed and/or encrypted custom header it is unable to verify the signature.</span></span> <span data-ttu-id="c794e-108">To obejście pozwala uniknąć błędu kanonizacji, umożliwia współdziałanie z usługami nieobsługującymi usług WCF, ale nie uniemożliwia współdziałania z usługami WCF.</span><span class="sxs-lookup"><span data-stu-id="c794e-108">This workaround avoids the canonicalization bug, allows interoperability with non-WCF services, but does not prevent interoperability with WCF services.</span></span>  
  
## <a name="defining-the-custom-header"></a><span data-ttu-id="c794e-109">Definiowanie niestandardowego nagłówka</span><span class="sxs-lookup"><span data-stu-id="c794e-109">Defining the custom header</span></span>  
 <span data-ttu-id="c794e-110">Niestandardowe nagłówki są definiowane przez zdefiniowanie kontraktu komunikatu i oznaczenie elementów członkowskich, które mają być wysyłane jako nagłówki z <xref:System.ServiceModel.MessageHeaderAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="c794e-110">Custom headers are defined by defining a message contract and marking the members you want to be sent as headers with a <xref:System.ServiceModel.MessageHeaderAttribute> attribute.</span></span> <span data-ttu-id="c794e-111">Aby obejść problem z kanonizacją, należy upewnić się, że Serializator XML deklaruje przestrzeń nazw dla niestandardowego nagłówka z prefiksem zamiast deklaracji domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c794e-111">To work around the canonicalization bug you must ensure that the XML serializer declares the namespace for the custom header with a prefix instead of a default namespace declaration.</span></span> <span data-ttu-id="c794e-112">Poniższy kod pokazuje, jak zdefiniować typ danych, który będzie używany jako nagłówek komunikatu z prawidłową deklaracją przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c794e-112">The following code shows how to define the data type that will be used as a message header with the correct namespace declaration.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="c794e-113">Ten kod deklaruje nowy typ o `msgHeaderElement` nazwie, który zostanie Zserializowany za pomocą serializatora XML.</span><span class="sxs-lookup"><span data-stu-id="c794e-113">This code declares a new type called `msgHeaderElement` that will be serialized with the XML Serializer.</span></span> <span data-ttu-id="c794e-114">Gdy wystąpienie tego typu jest serializowane, zdefiniuje przestrzeń nazw z prefiksem "h", co spowoduje obejście błędu kanonizacji.</span><span class="sxs-lookup"><span data-stu-id="c794e-114">When an instance of this type is serialized, it will define a namespace with an ‘h’ prefix, thus working around the canonicalization bug.</span></span>  <span data-ttu-id="c794e-115">Następnie kontrakt wiadomości zdefiniuje wystąpienie `msgHeaderElement` i oznaczy go <xref:System.ServiceModel.MessageHeaderAttribute> atrybutem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c794e-115">The message contract would then define an instance of `msgHeaderElement` and mark it with the <xref:System.ServiceModel.MessageHeaderAttribute> attribute as shown in the following example.</span></span>  
  
```csharp
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c794e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c794e-116">See also</span></span>

- [<span data-ttu-id="c794e-117">Domyślny kontrakt komunikatów</span><span class="sxs-lookup"><span data-stu-id="c794e-117">Default Message Contract</span></span>](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [<span data-ttu-id="c794e-118">Kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="c794e-118">Message Contracts</span></span>](../../../../docs/framework/wcf/samples/message-contracts.md)
- [<span data-ttu-id="c794e-119">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="c794e-119">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
