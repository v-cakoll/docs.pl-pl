---
title: Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer
description: Dowiedz się więcej o sposobie zmiany serializacji znaków sterujących w celu zapewnienia zgodności z ECMAScript V6 i V8 w .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475388"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="bfaea-103">Środki zaradcze: serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="bfaea-103">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="bfaea-104">Począwszy od .NET Framework 4,7, sposób, w jaki znaki sterujące są serializowane z, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony na zgodny z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="bfaea-104">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="bfaea-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="bfaea-105">Impact</span></span>

<span data-ttu-id="bfaea-106">W .NET Framework 4.6.2 i starszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializacji niektórych specjalnych znaków kontroli, takich jak `\b` , `\f` i `\t` , w sposób zgodny z standardami ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="bfaea-106">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="bfaea-107">W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 Serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="bfaea-107">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="bfaea-108">Dotyczy to następujących interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="bfaea-108">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="bfaea-109">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="bfaea-109">Mitigation</span></span>

<span data-ttu-id="bfaea-110">W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 to zachowanie jest domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="bfaea-110">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="bfaea-111">Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="bfaea-111">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="bfaea-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfaea-112">See also</span></span>

- [<span data-ttu-id="bfaea-113">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="bfaea-113">Application compatibility</span></span>](application-compatibility.md)
