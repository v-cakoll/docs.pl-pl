---
ms.openlocfilehash: f87b70708398226516ab5eac32c24a9fc2c1106b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615739"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a><span data-ttu-id="5f874-101">Element XmlWriter zwraca dla nieprawidłowych par surogatów</span><span class="sxs-lookup"><span data-stu-id="5f874-101">XmlWriter throws on invalid surrogate pairs</span></span>

#### <a name="details"></a><span data-ttu-id="5f874-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="5f874-102">Details</span></span>

<span data-ttu-id="5f874-103">W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.5.2 lub poprzednich wersji, zapisanie nieprawidłowej pary dwuskładnikowej przy użyciu obsługi rezerwy wyjątku nie zawsze zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5f874-103">For apps that target the .NET Framework 4.5.2 or previous versions, writing an invalid surrogate pair using exception fallback handling does not always throw an exception.</span></span> <span data-ttu-id="5f874-104">W przypadku aplikacji przeznaczonych dla .NET Framework 4,6 Próba zapisania nieprawidłowej pary dwuskładnikowej zgłasza <xref:System.ArgumentException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="5f874-104">For apps that target the .NET Framework 4.6, attempting to write an invalid surrogate pair throws an <xref:System.ArgumentException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5f874-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="5f874-105">Suggestion</span></span>

<span data-ttu-id="5f874-106">W razie potrzeby można uniknąć tego przerwania, przeznaczoną dla .NET Framework 4.5.2 lub wcześniejszym.</span><span class="sxs-lookup"><span data-stu-id="5f874-106">If necessary, this break can be avoided by targeting the .NET Framework 4.5.2 or earlier.</span></span> <span data-ttu-id="5f874-107">Alternatywnie można wstępnie przetworzyć nieprawidłowe pary surogatów w prawidłowym kodzie XML przed ich zapisaniem.</span><span class="sxs-lookup"><span data-stu-id="5f874-107">Alternatively, invalid surrogate pairs can be pre-processed into valid xml prior to writing them.</span></span>

| <span data-ttu-id="5f874-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5f874-108">Name</span></span>    | <span data-ttu-id="5f874-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="5f874-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5f874-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="5f874-110">Scope</span></span>   | <span data-ttu-id="5f874-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="5f874-111">Edge</span></span>        |
| <span data-ttu-id="5f874-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="5f874-112">Version</span></span> | <span data-ttu-id="5f874-113">4.6</span><span class="sxs-lookup"><span data-stu-id="5f874-113">4.6</span></span>         |
| <span data-ttu-id="5f874-114">Typ</span><span class="sxs-lookup"><span data-stu-id="5f874-114">Type</span></span>    | <span data-ttu-id="5f874-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="5f874-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5f874-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5f874-116">Affected APIs</span></span>

- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType>
