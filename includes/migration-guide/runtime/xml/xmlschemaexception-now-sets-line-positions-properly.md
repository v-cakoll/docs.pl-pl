---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620502"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="eda74-101">Sqlschemaexception teraz ustawia prawidłowo pozycje wierszy</span><span class="sxs-lookup"><span data-stu-id="eda74-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="eda74-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="eda74-102">Details</span></span>

<span data-ttu-id="eda74-103">Jeśli <xref:System.Xml.Linq.LoadOptions.SetLineInfo> wartość jest przenoszona do metody Load i wystąpi błąd walidacji, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> <xref:System.Xml.Schema.XmlSchemaException.LinePosition> właściwości i zawierają teraz informacje o wierszu.</span><span class="sxs-lookup"><span data-stu-id="eda74-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eda74-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="eda74-104">Suggestion</span></span>

<span data-ttu-id="eda74-105">Kod obsługi wyjątków, który przyjmuje <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nie zostanie ustawiony, należy zaktualizować, ponieważ te właściwości będą teraz prawidłowo ustawione, gdy SetLineInfo jest używany podczas ładowania kodu XML.</span><span class="sxs-lookup"><span data-stu-id="eda74-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="eda74-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="eda74-106">Name</span></span>    | <span data-ttu-id="eda74-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="eda74-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eda74-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="eda74-108">Scope</span></span>   |<span data-ttu-id="eda74-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="eda74-109">Edge</span></span>|
|<span data-ttu-id="eda74-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="eda74-110">Version</span></span>|<span data-ttu-id="eda74-111">4.5</span><span class="sxs-lookup"><span data-stu-id="eda74-111">4.5</span></span>|
|<span data-ttu-id="eda74-112">Typ</span><span class="sxs-lookup"><span data-stu-id="eda74-112">Type</span></span>|<span data-ttu-id="eda74-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="eda74-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eda74-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="eda74-114">Affected APIs</span></span>

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
