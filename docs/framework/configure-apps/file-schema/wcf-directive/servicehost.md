---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3102ae8d8c28be43883eeaff6c4f829b355384a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111400"
---
# <a name="servicehost"></a><span data-ttu-id="26256-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="26256-101">\@ServiceHost</span></span>
<span data-ttu-id="26256-102">Kojarzy fabryka użyta do wyprodukowania hosta usługi przy użyciu usługi hostowane i innych aspektów programowania wymagane w celu uzyskania dostępu lub skompilować kod hostingu z pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="26256-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26256-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="26256-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="26256-104">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="26256-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="26256-105">Usługa</span><span class="sxs-lookup"><span data-stu-id="26256-105">Service</span></span>  
 <span data-ttu-id="26256-106">Nazwa typu CLR usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="26256-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="26256-107">Powinna to być kwalifikowana nazwa typu, który implementuje jedną lub więcej kontaktów usługi.</span><span class="sxs-lookup"><span data-stu-id="26256-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="26256-108">Fabryka</span><span class="sxs-lookup"><span data-stu-id="26256-108">Factory</span></span>  
 <span data-ttu-id="26256-109">Nazwa typu CLR fabryki hostów usług, które są używane do utworzenia wystąpienia hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="26256-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="26256-110">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="26256-110">This attribute is optional.</span></span> <span data-ttu-id="26256-111">Jeśli nie zostanie podany, domyślna <xref:System.ServiceModel.Activation.ServiceHostFactory> jest używany, która zwraca wystąpienie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="26256-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="26256-112">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="26256-112">Debug</span></span>  
 <span data-ttu-id="26256-113">Wskazuje, czy usługa Windows Communication Foundation (WCF) powinna być skompilowana przy użyciu symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="26256-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> `true` <span data-ttu-id="26256-114">Jeśli usługa WCF powinna być skompilowana przy użyciu symboli debugowania; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="26256-114">if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="26256-115">Język</span><span class="sxs-lookup"><span data-stu-id="26256-115">Language</span></span>  
 <span data-ttu-id="26256-116">Określa język używany podczas kompilowania kodu wbudowanego w pliku (SVC).</span><span class="sxs-lookup"><span data-stu-id="26256-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="26256-117">Wartość może reprezentować dowolny. Obsługiwane NET języka, w tym C#, VB i JS, które odwołują się odpowiednio do języka C#, Visual Basic .NET i JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="26256-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="26256-118">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="26256-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="26256-119">Plik CodeBehind</span><span class="sxs-lookup"><span data-stu-id="26256-119">CodeBehind</span></span>  
 <span data-ttu-id="26256-120">Określa plik źródłowy, który implementuje usługi XML sieci Web, gdy klasa, która implementuje usługi XML sieci Web nie znajduje się w tym samym pliku i nie został skompilowany w zestawie i umieszczane w katalogu \Bin.</span><span class="sxs-lookup"><span data-stu-id="26256-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26256-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26256-121">Remarks</span></span>  
 <span data-ttu-id="26256-122"><xref:System.ServiceModel.ServiceHost> Używane do hostowania usługi jest punktem rozszerzalność w modelu programowania Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="26256-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="26256-123">Wzorzec fabryki jest używany do utworzenia wystąpienia <xref:System.ServiceModel.ServiceHost> ponieważ, potencjalnie, typem polimorficznym, środowisko hostingu nie należy bezpośrednio wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="26256-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="26256-124">Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> do utworzenia wystąpienia <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="26256-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="26256-125">Ale możesz podać własne fabryki (taki, który zwraca pochodnej hosta), określając nazwę typu CLR fabryki implementacji w [ \@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="26256-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="26256-126">Aby użyć własnych niestandardowych usługi fabryka hostów zamiast domyślną fabrykę, wystarczy podać nazwę typu w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="26256-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="26256-127">Zachowaj jak implementacje fabryki.</span><span class="sxs-lookup"><span data-stu-id="26256-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="26256-128">Jeśli masz wiele logikę niestandardową, Twój kod jest bardziej wielokrotnego użytku, jeżeli umieścisz tej logiki wewnątrz hosta zamiast w fabryce.</span><span class="sxs-lookup"><span data-stu-id="26256-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="26256-129">Na przykład, aby włączyć punkt końcowy interfejsu AJAX w celu `MyService`, określ <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dla wartości `Factory` atrybutu zamiast domyślnego <xref:System.ServiceModel.Activation.ServiceHostFactory>w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy jako pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="26256-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26256-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="26256-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26256-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26256-131">See also</span></span>

- [<span data-ttu-id="26256-132">Niestandardowy host usługi</span><span class="sxs-lookup"><span data-stu-id="26256-132">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
