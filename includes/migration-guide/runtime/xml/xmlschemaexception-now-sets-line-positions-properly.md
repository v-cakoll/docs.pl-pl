---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379623"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="99aef-101">Xmlschemaexception — teraz Ustawia pozycje wiersza prawidłowo</span><span class="sxs-lookup"><span data-stu-id="99aef-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="99aef-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="99aef-102">Details</span></span>|<span data-ttu-id="99aef-103">Jeśli <xref:System.Xml.Linq.LoadOptions.SetLineInfo> wartość jest przekazywana do metody obciążenia i wystąpi błąd sprawdzania poprawności, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> właściwości zawierają teraz informacje wiersza.</span><span class="sxs-lookup"><span data-stu-id="99aef-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="99aef-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="99aef-104">Suggestion</span></span>|<span data-ttu-id="99aef-105">Kod obsługi wyjątków, który przyjmuje <xref:System.Xml.Schema.XmlSchemaException.LineNumber> i <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nie będzie zaktualizować zestawu, ponieważ te właściwości można lokacji ustawi teraz poprawnie stosowania SetLineInfo podczas ładowania danych XML.</span><span class="sxs-lookup"><span data-stu-id="99aef-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="99aef-106">Scope</span><span class="sxs-lookup"><span data-stu-id="99aef-106">Scope</span></span>|<span data-ttu-id="99aef-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="99aef-107">Edge</span></span>|
|<span data-ttu-id="99aef-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="99aef-108">Version</span></span>|<span data-ttu-id="99aef-109">4.5</span><span class="sxs-lookup"><span data-stu-id="99aef-109">4.5</span></span>|
|<span data-ttu-id="99aef-110">Typ</span><span class="sxs-lookup"><span data-stu-id="99aef-110">Type</span></span>|<span data-ttu-id="99aef-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="99aef-111">Runtime</span></span>|
|<span data-ttu-id="99aef-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="99aef-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
