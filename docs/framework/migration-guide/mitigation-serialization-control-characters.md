---
title: 'Ograniczenie: Serializacja znaki kontrolne z elementu DataContractJsonSerializer'
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6da580d208736a64e2094f701fb4c1241a488322
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="3e316-102">Ograniczenie: Serializacja znaki kontrolne z elementu DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="3e316-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="3e316-103">W programie .NET Framework 4.7, sposób, w których kontroli znaki są serializowane z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> została zmieniona z wersja języka ECMAScript 6 i V8.</span><span class="sxs-lookup"><span data-stu-id="3e316-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="3e316-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="3e316-104">Impact</span></span>

<span data-ttu-id="3e316-105">.NET framework 4.6.2 i wcześniejszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializować niektóre znaki kontrolne specjalnych, takich jak `\b`, `\f`, i `\t`, w sposób zgodny ze standardami wersja języka ECMAScript 6 i V8.</span><span class="sxs-lookup"><span data-stu-id="3e316-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="3e316-106">W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework w programie .NET Framework 4.7 serializacji te znaki kontrolne jest zgodny z wersja języka ECMAScript 6 i V8.</span><span class="sxs-lookup"><span data-stu-id="3e316-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="3e316-107">Uwzględnione są następujące:</span><span class="sxs-lookup"><span data-stu-id="3e316-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="3e316-108">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="3e316-108">Mitigation</span></span>

<span data-ttu-id="3e316-109">W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework w programie .NET Framework 4.7 to zachowanie jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="3e316-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="3e316-110">Jeśli to zachowanie nie jest pożądane, można zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="3e316-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="3e316-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e316-111">See also</span></span>
[<span data-ttu-id="3e316-112">Zmiany w przekierowywaniu w programie .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="3e316-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
