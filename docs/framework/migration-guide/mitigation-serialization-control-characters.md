---
title: Środki zaradcze Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b26c8cc01b7af1c3b345d2f274a1d25a19d689
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789847"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="d6108-102">Środki zaradcze Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="d6108-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="d6108-103">Począwszy od .NET Framework 4,7, sposób, w jaki znaki sterujące są serializowane z, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony, aby był zgodny z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="d6108-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="d6108-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="d6108-104">Impact</span></span>

<span data-ttu-id="d6108-105">W programie .NET Framework <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 4.6.2 i starszych wersjach nie serializacji niektórych specjalnych znaków kontroli, takich jak `\b`, `\f`, i `\t`w sposób zgodny z standardami ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="d6108-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="d6108-106">W przypadku aplikacji przeznaczonych dla wersji .NET Framework rozpoczynających się od .NET Framework 4,7, serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="d6108-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="d6108-107">Dotyczy to następujących interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="d6108-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="d6108-108">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="d6108-108">Mitigation</span></span>

<span data-ttu-id="d6108-109">W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od .NET Framework 4,7 to zachowanie jest domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="d6108-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="d6108-110">Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji pliku App. config lub Web. config:</span><span class="sxs-lookup"><span data-stu-id="d6108-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="d6108-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6108-111">See also</span></span>

- [<span data-ttu-id="d6108-112">Przekierowywanie zmian w .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="d6108-112">Retargeting Changes in the .NET Framework 4.7</span></span>](retargeting-changes-in-the-net-framework-4-7.md)
