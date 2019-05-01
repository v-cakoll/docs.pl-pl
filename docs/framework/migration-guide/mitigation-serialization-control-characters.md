---
title: 'Środki zaradcze: Serializacja znaki kontrolne przy użyciu elementu DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3355841298e039652eb81918eac98186c1a1f833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871374"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="73660-102">Środki zaradcze: Serializacja znaki kontrolne przy użyciu elementu DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="73660-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="73660-103">Począwszy od .NET Framework 4.7, w sposób, w które określają znaki są było serializować ją przy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> został zmieniony na odpowiadają wersji ECMAScript 6 i V8.</span><span class="sxs-lookup"><span data-stu-id="73660-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="73660-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="73660-104">Impact</span></span>

<span data-ttu-id="73660-105">W .NET framework 4.6.2 i wcześniejszymi wersjami <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie serializować niektóre znaki specjalne kontrolki, takie jak `\b`, `\f`, i `\t`, w sposób, który był zgodny ze standardami w wersji ECMAScript 6 i V8.</span><span class="sxs-lookup"><span data-stu-id="73660-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="73660-106">W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.7 serializacji te znaki kontrolne jest zgodny z wersji ECMAScript 6 i V8.</span><span class="sxs-lookup"><span data-stu-id="73660-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="73660-107">Uwzględnione są następujące funkcje interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="73660-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="73660-108">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="73660-108">Mitigation</span></span>

<span data-ttu-id="73660-109">W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.7 to zachowanie jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="73660-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="73660-110">Jeśli to zachowanie nie jest pożądane, można zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="73660-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="73660-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73660-111">See also</span></span>

- [<span data-ttu-id="73660-112">Zmiany retargetingu w programie .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="73660-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
