---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787803"
---
# <a name="servicehost"></a><span data-ttu-id="ab8d6-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="ab8d6-101">\@ServiceHost</span></span>

<span data-ttu-id="ab8d6-102">Kojarzy fabrykę używaną do tworzenia hosta usługi z usługą, która ma być hostowana, i innych aspektów programistycznych wymaganych do uzyskania dostępu lub skompilowania kodu hostingu podanego w pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab8d6-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab8d6-103">Syntax</span></span>

```xml
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a><span data-ttu-id="ab8d6-104">{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ab8d6-104">Attributes</span></span>

### <a name="service"></a><span data-ttu-id="ab8d6-105">NDES</span><span class="sxs-lookup"><span data-stu-id="ab8d6-105">Service</span></span>

<span data-ttu-id="ab8d6-106">Nazwa typu CLR hostowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="ab8d6-107">Powinna to być kwalifikowana nazwa typu, który implementuje co najmniej jeden kontakt usługi.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>

### <a name="factory"></a><span data-ttu-id="ab8d6-108">indywidual</span><span class="sxs-lookup"><span data-stu-id="ab8d6-108">Factory</span></span>

<span data-ttu-id="ab8d6-109">Nazwa typu CLR fabryki hosta usługi użyta do utworzenia wystąpienia hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="ab8d6-110">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-110">This attribute is optional.</span></span> <span data-ttu-id="ab8d6-111">Jeśli nie zostanie określony, zostanie użyta domyślna <xref:System.ServiceModel.Activation.ServiceHostFactory>, która zwraca wystąpienie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

### <a name="debug"></a><span data-ttu-id="ab8d6-112">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ab8d6-112">Debug</span></span>

<span data-ttu-id="ab8d6-113">Wskazuje, czy usługa Windows Communication Foundation (WCF) powinna być skompilowana przy użyciu symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="ab8d6-114">`true`, jeśli usługa WCF powinna być skompilowana przy użyciu symboli debugowania; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>

### <a name="language"></a><span data-ttu-id="ab8d6-115">Język</span><span class="sxs-lookup"><span data-stu-id="ab8d6-115">Language</span></span>

<span data-ttu-id="ab8d6-116">Określa język używany podczas kompilowania całego kodu śródwierszowego w pliku (. svc).</span><span class="sxs-lookup"><span data-stu-id="ab8d6-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="ab8d6-117">Wartości mogą reprezentować dowolne. Język obsługiwany w sieci, w tym `C#`, `VB`i `JS`, który odwołuje C#się odpowiednio do, Visual Basic i JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="ab8d6-118">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-118">This attribute is optional.</span></span>

### <a name="codebehind"></a><span data-ttu-id="ab8d6-119">Plik CodeBehind</span><span class="sxs-lookup"><span data-stu-id="ab8d6-119">CodeBehind</span></span>

<span data-ttu-id="ab8d6-120">Określa plik źródłowy, który implementuje usługę sieci Web XML, gdy Klasa implementująca usługę XML sieci Web nie znajduje się w tym samym pliku i nie została skompilowana do zestawu i umieszczona w katalogu *\Bin* .</span><span class="sxs-lookup"><span data-stu-id="ab8d6-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the *\Bin* directory.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab8d6-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab8d6-121">Remarks</span></span>

<span data-ttu-id="ab8d6-122"><xref:System.ServiceModel.ServiceHost> używany do hostowania usługi jest punktem rozszerzalności w modelu programowania Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ab8d6-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="ab8d6-123">Wzorzec fabryki służy do tworzenia wystąpienia <xref:System.ServiceModel.ServiceHost>, ponieważ jest to, potencjalnie, typ polimorficzny, że środowisko hostingu nie powinno bezpośrednio tworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>

<span data-ttu-id="ab8d6-124">Domyślna implementacja używa <xref:System.ServiceModel.Activation.ServiceHostFactory> do utworzenia wystąpienia <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="ab8d6-125">Można jednak zapewnić własną fabrykę (taką, która zwraca hosta pochodnego), określając nazwę typu CLR implementacji fabryki w dyrektywie `@ServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the `@ServiceHost` directive.</span></span>

<span data-ttu-id="ab8d6-126">Aby korzystać z własnej fabryki hosta usługi niestandardowej zamiast fabryki domyślnej, wystarczy podać nazwę typu w dyrektywie `@ServiceHost` w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-126">To use you own custom service host factory instead of the default factory, just provide the type name in the `@ServiceHost` directive as follows.</span></span>

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

<span data-ttu-id="ab8d6-127">W miarę możliwości Zachowaj implementacje fabryk.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="ab8d6-128">Jeśli masz wiele logiki niestandardowej, kod jest większy do wielokrotnego użytku, jeśli zostanie umieszczony w obrębie hosta zamiast fabryki.</span><span class="sxs-lookup"><span data-stu-id="ab8d6-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>

<span data-ttu-id="ab8d6-129">Na przykład aby włączyć punkt końcowy z obsługą technologii AJAX dla `MyService`, należy określić <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dla wartości atrybutu `Factory` zamiast domyślnego <xref:System.ServiceModel.Activation.ServiceHostFactory>, w dyrektywie `@ServiceHost`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ab8d6-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the `@ServiceHost` directive as shown in the following example:</span></span>

```xml
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a><span data-ttu-id="ab8d6-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab8d6-130">See also</span></span>

- [<span data-ttu-id="ab8d6-131">Niestandardowy host usługi</span><span class="sxs-lookup"><span data-stu-id="ab8d6-131">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
