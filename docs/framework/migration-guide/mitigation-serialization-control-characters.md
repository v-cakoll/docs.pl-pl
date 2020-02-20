---
title: Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b6468bc4ae37765d969a1f92b16967cc656ab7ff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452633"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="287fb-102">Środki zaradcze: serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="287fb-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="287fb-103">Począwszy od .NET Framework 4,7, sposób, w jaki znaki sterujące są serializowane z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony tak, aby był zgodny z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="287fb-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="287fb-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="287fb-104">Impact</span></span>

<span data-ttu-id="287fb-105">W .NET Framework 4.6.2 i starszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializować niektórych specjalnych znaków sterujących, takich jak `\b`, `\f`i `\t`, w sposób zgodny z standardami ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="287fb-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="287fb-106">W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 Serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="287fb-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="287fb-107">Dotyczy to następujących interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="287fb-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="287fb-108">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="287fb-108">Mitigation</span></span>

<span data-ttu-id="287fb-109">W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 to zachowanie jest domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="287fb-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="287fb-110">Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do sekcji `<runtime>` pliku App. config lub Web. config:</span><span class="sxs-lookup"><span data-stu-id="287fb-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="287fb-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="287fb-111">See also</span></span>

- [<span data-ttu-id="287fb-112">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="287fb-112">Application compatibility</span></span>](application-compatibility.md)
