---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: a56fb1bb9395425222347914fe3f4c17f1a451b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920338"
---
# <a name="servicehost"></a><span data-ttu-id="c3ac7-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="c3ac7-101">\@ServiceHost</span></span>
<span data-ttu-id="c3ac7-102">Kojarzy fabrykę używaną do tworzenia hosta usługi z usługą, która ma być hostowana, i innych aspektów programistycznych wymaganych do uzyskania dostępu lub skompilowania kodu hostingu podanego w pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ac7-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3ac7-103">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="c3ac7-104">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3ac7-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="c3ac7-105">Usługa</span><span class="sxs-lookup"><span data-stu-id="c3ac7-105">Service</span></span>  
 <span data-ttu-id="c3ac7-106">Nazwa typu CLR hostowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="c3ac7-107">Powinna to być kwalifikowana nazwa typu, który implementuje co najmniej jeden kontakt usługi.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="c3ac7-108">Indywidual</span><span class="sxs-lookup"><span data-stu-id="c3ac7-108">Factory</span></span>  
 <span data-ttu-id="c3ac7-109">Nazwa typu CLR fabryki hosta usługi użyta do utworzenia wystąpienia hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="c3ac7-110">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-110">This attribute is optional.</span></span> <span data-ttu-id="c3ac7-111">Jeśli nie zostanie określony, zostanie <xref:System.ServiceModel.Activation.ServiceHostFactory> użyta wartość domyślna, która zwraca <xref:System.ServiceModel.ServiceHost>wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="c3ac7-112">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c3ac7-112">Debug</span></span>  
 <span data-ttu-id="c3ac7-113">Wskazuje, czy usługa Windows Communication Foundation (WCF) powinna być skompilowana przy użyciu symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="c3ac7-114">`true`Jeśli usługa WCF powinna być skompilowana przy użyciu symboli debugowania; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="c3ac7-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="c3ac7-115">Język</span><span class="sxs-lookup"><span data-stu-id="c3ac7-115">Language</span></span>  
 <span data-ttu-id="c3ac7-116">Określa język używany podczas kompilowania całego kodu śródwierszowego w pliku (. svc).</span><span class="sxs-lookup"><span data-stu-id="c3ac7-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="c3ac7-117">Wartości mogą reprezentować dowolne. Język obsługiwany w sieci, w C#tym VB i JS, który odnosi się C#odpowiednio do, Visual Basic .NET i JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-117">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="c3ac7-118">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="c3ac7-119">Plik CodeBehind</span><span class="sxs-lookup"><span data-stu-id="c3ac7-119">CodeBehind</span></span>  
 <span data-ttu-id="c3ac7-120">Określa plik źródłowy, który implementuje usługę sieci Web XML, gdy Klasa implementująca usługę XML sieci Web nie znajduje się w tym samym pliku i nie została skompilowana do zestawu i umieszczona w katalogu \Bin.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3ac7-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3ac7-121">Remarks</span></span>  
 <span data-ttu-id="c3ac7-122"><xref:System.ServiceModel.ServiceHost> Używany do hostowania usługi jest punktem rozszerzalności w modelu programowania Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c3ac7-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="c3ac7-123">Wzorzec fabryki służy do tworzenia wystąpienia <xref:System.ServiceModel.ServiceHost> elementu, ponieważ jest to, potencjalnie, typ polimorficzny, że środowisko hostingu nie powinno bezpośrednio tworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="c3ac7-124">Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> do tworzenia <xref:System.ServiceModel.ServiceHost>wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="c3ac7-125">Można jednak zapewnić własną fabrykę (taką, która zwraca hosta pochodnego), określając nazwę typu CLR implementacji fabryki w [ \@](servicehost.md) dyrektywie ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="c3ac7-126">Aby korzystać z własnej fabryki hosta usługi niestandardowej zamiast fabryki domyślnej, wystarczy podać nazwę typu w [@ServiceHost](servicehost.md) dyrektywie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c3ac7-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="c3ac7-127">W miarę możliwości Zachowaj implementacje fabryk.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="c3ac7-128">Jeśli masz wiele logiki niestandardowej, kod jest większy do wielokrotnego użytku, jeśli zostanie umieszczony w obrębie hosta zamiast fabryki.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="c3ac7-129">Na przykład, aby włączyć punkt końcowy z obsługą technologii `MyService`AJAX dla programu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , należy określić jako wartość `Factory` atrybutu zamiast domyślnego <xref:System.ServiceModel.Activation.ServiceHostFactory>, w [@ServiceHost](servicehost.md) dyrektywie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c3ac7-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3ac7-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3ac7-130">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3ac7-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3ac7-131">See also</span></span>

- [<span data-ttu-id="c3ac7-132">Niestandardowy host usługi</span><span class="sxs-lookup"><span data-stu-id="c3ac7-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
