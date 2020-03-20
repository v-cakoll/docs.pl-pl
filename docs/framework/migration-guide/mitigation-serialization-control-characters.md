---
title: Serializacja znaków kontrolnych za pomocą datacontractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181209"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="fd37c-102">Łagodzenie: Serializacja znaków kontrolnych za pomocą datacontractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="fd37c-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="fd37c-103">Począwszy od programu .NET Framework 4.7, sposób, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> w jaki znaki sterujące są serializowane z został zmieniony, aby były zgodne z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="fd37c-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="fd37c-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="fd37c-104">Impact</span></span>

<span data-ttu-id="fd37c-105">W programach .NET Framework 4.6.2 i wcześniejszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie `\b`serializowały niektórych znaków sterujących specjalnych, takich jak , `\f`i `\t`, w sposób zgodny ze standardami ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="fd37c-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="fd37c-106">W przypadku aplikacji docelowych wersji programu .NET Framework, począwszy od platformy .NET Framework 4.7, serializacja tych znaków sterujących jest zgodna z systemami ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="fd37c-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="fd37c-107">Dotyczy to następujących interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="fd37c-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="fd37c-108">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="fd37c-108">Mitigation</span></span>

<span data-ttu-id="fd37c-109">W przypadku aplikacji docelowych wersji programu .NET Framework, począwszy od programu .NET Framework 4.7, to zachowanie jest domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="fd37c-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="fd37c-110">Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej `<runtime>` funkcji, dodając następujący wiersz do sekcji pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="fd37c-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="fd37c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd37c-111">See also</span></span>

- [<span data-ttu-id="fd37c-112">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="fd37c-112">Application compatibility</span></span>](application-compatibility.md)
