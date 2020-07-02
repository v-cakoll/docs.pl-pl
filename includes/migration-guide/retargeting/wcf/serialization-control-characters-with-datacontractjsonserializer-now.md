---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614791"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a><span data-ttu-id="e227d-101">Serializacja znaków sterujących za pomocą Klasa DataContractJsonSerializer jest teraz zgodna z ECMAScript V6 i V8</span><span class="sxs-lookup"><span data-stu-id="e227d-101">Serialization of control characters with DataContractJsonSerializer is now compatible with ECMAScript V6 and V8</span></span>

#### <a name="details"></a><span data-ttu-id="e227d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e227d-102">Details</span></span>

<span data-ttu-id="e227d-103">W .NET Framework 4.6.2 i starszych wersjach <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> nie serializacji niektórych specjalnych znaków kontroli, takich jak \b, \f i \t, w sposób zgodny z standardami ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="e227d-103">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> did not serialize some special control characters, such as \b, \f, and \t, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span> <span data-ttu-id="e227d-104">Począwszy od .NET Framework 4,7, serializacja tych znaków kontrolnych jest zgodna z ECMAScript V6 i V8.</span><span class="sxs-lookup"><span data-stu-id="e227d-104">Starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e227d-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e227d-105">Suggestion</span></span>

<span data-ttu-id="e227d-106">W przypadku aplikacji przeznaczonych dla .NET Framework 4,7 ta funkcja jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="e227d-106">For apps that target the .NET Framework 4.7, this feature is enabled by default.</span></span> <span data-ttu-id="e227d-107">Jeśli to zachowanie nie jest pożądane, możesz zrezygnować z tej funkcji, dodając następujący wiersz do `<runtime>` sekcji pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="e227d-107">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| <span data-ttu-id="e227d-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e227d-108">Name</span></span>    | <span data-ttu-id="e227d-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="e227d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e227d-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="e227d-110">Scope</span></span>   | <span data-ttu-id="e227d-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="e227d-111">Edge</span></span>        |
| <span data-ttu-id="e227d-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="e227d-112">Version</span></span> | <span data-ttu-id="e227d-113">4,7</span><span class="sxs-lookup"><span data-stu-id="e227d-113">4.7</span></span>         |
| <span data-ttu-id="e227d-114">Typ</span><span class="sxs-lookup"><span data-stu-id="e227d-114">Type</span></span>    | <span data-ttu-id="e227d-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="e227d-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e227d-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e227d-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
