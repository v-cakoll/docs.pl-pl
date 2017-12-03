---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10f7a0b077fb50149ad60034607eec413e774ee6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicehost"></a>@ServiceHost
<span data-ttu-id="78c70-101">Kojarzy fabryka użyta do wyprodukowania hosta usługi z usługą ma być obsługiwana i inne aspekty programowania wymagane do uzyskania dostępu lub skompilować hostingu kod zawarty w pliku svc.</span><span class="sxs-lookup"><span data-stu-id="78c70-101">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78c70-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="78c70-102">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="78c70-103">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="78c70-103">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="78c70-104">Usługa</span><span class="sxs-lookup"><span data-stu-id="78c70-104">Service</span></span>  
 <span data-ttu-id="78c70-105">Nazwa typu CLR usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="78c70-105">The CLR type name of the service hosted.</span></span> <span data-ttu-id="78c70-106">Powinna to być kwalifikowaną nazwę typu, który implementuje co najmniej jeden kontakty usługi.</span><span class="sxs-lookup"><span data-stu-id="78c70-106">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="78c70-107">Fabryka</span><span class="sxs-lookup"><span data-stu-id="78c70-107">Factory</span></span>  
 <span data-ttu-id="78c70-108">Nazwa typu CLR fabryki hostów usług służący do uruchamiania usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="78c70-108">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="78c70-109">Ten atrybut jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="78c70-109">This attribute is optional.</span></span> <span data-ttu-id="78c70-110">Jeśli zostanie określona, domyślnie <xref:System.ServiceModel.Activation.ServiceHostFactory> jest używana, która zwraca wystąpienie klasy <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="78c70-110">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="78c70-111">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="78c70-111">Debug</span></span>  
 <span data-ttu-id="78c70-112">Wskazuje, czy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi ma być kompilowana przy użyciu symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="78c70-112">Indicates whether the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service should be compiled with debug symbols.</span></span> <span data-ttu-id="78c70-113">`true`Jeśli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi powinny być skompilowanych przy użyciu symboli debugowania; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="78c70-113">`true` if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="78c70-114">Język</span><span class="sxs-lookup"><span data-stu-id="78c70-114">Language</span></span>  
 <span data-ttu-id="78c70-115">Określa język używany podczas kompilowania kodu wbudowanego w pliku (SVC).</span><span class="sxs-lookup"><span data-stu-id="78c70-115">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="78c70-116">Wartości może reprezentować żadnego. Obsługiwane NET język, w tym C#, VB i JS, które dotyczą odpowiednio C#, Visual Basic .NET i JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="78c70-116">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="78c70-117">Ten atrybut jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="78c70-117">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="78c70-118">Plik CodeBehind</span><span class="sxs-lookup"><span data-stu-id="78c70-118">CodeBehind</span></span>  
 <span data-ttu-id="78c70-119">Określa plik źródłowy, który implementuje usługi XML sieci Web, gdy klasa, która implementuje usługi XML sieci Web nie znajduje się w tym samym pliku, a nie został skompilowany w zestawie i umieszczane w katalogu \Bin.</span><span class="sxs-lookup"><span data-stu-id="78c70-119">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78c70-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78c70-120">Remarks</span></span>  
 <span data-ttu-id="78c70-121"><xref:System.ServiceModel.ServiceHost> Używane do obsługi usługi jest punktem rozszerzalności w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] model programowania.</span><span class="sxs-lookup"><span data-stu-id="78c70-121">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] programming model.</span></span> <span data-ttu-id="78c70-122">Wzorzec fabryki służy do tworzenia wystąpienia <xref:System.ServiceModel.ServiceHost> , dlatego potencjalnie, typ polimorficzny środowisko macierzyste nie należy bezpośrednio wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="78c70-122">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="78c70-123">Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> można utworzyć wystąpienia <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="78c70-123">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="78c70-124">Ale możesz podać własne fabryki (taki, który zwraca pochodnej hosta), określając nazwę typu CLR fabryki implementacji w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="78c70-124">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="78c70-125">Aby użyć własnych niestandardowych usługi fabryka hostów zamiast domyślną fabrykę, wystarczy podać nazwę typu w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="78c70-125">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="78c70-126">Zachowaj jak implementacje fabryki.</span><span class="sxs-lookup"><span data-stu-id="78c70-126">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="78c70-127">Jeśli masz wiele niestandardowej logiki kodu jest bardziej wielokrotnego użytku, jeśli umieść ten logikę w sieci hosta zamiast w fabryce.</span><span class="sxs-lookup"><span data-stu-id="78c70-127">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="78c70-128">Na przykład, aby włączyć punkt końcowy interfejsu AJAX dla `MyService`, określ <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dla wartości `Factory` atrybutu, zamiast domyślnej <xref:System.ServiceModel.Activation.ServiceHostFactory>w [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy jako pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="78c70-128">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78c70-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="78c70-129">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78c70-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78c70-130">See Also</span></span>  
 [<span data-ttu-id="78c70-131">Niestandardowy Host usługi</span><span class="sxs-lookup"><span data-stu-id="78c70-131">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
