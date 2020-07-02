---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620430"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="1b24e-101">FlowDocument może wyświetlić dodatkowy wiersz tekstu</span><span class="sxs-lookup"><span data-stu-id="1b24e-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="1b24e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1b24e-102">Details</span></span>

<span data-ttu-id="1b24e-103">W niektórych przypadkach <xref:System.Windows.Documents.FlowDocument> element będzie wyświetlał dodatkowy wiersz tekstu podczas uruchamiania na .NET Framework 4,5 w porównaniu do sposobu, w jaki jest wyświetlany, gdy jest uruchamiany na .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="1b24e-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="1b24e-104">Nie istnieją znane przypadki zmiany, które powodują słabą i nieillegibly tekstu, ale może to spowodować, że tekst jest wyświetlany wcześniej z <xref:System.Windows.Documents.FlowDocument> widoku.</span><span class="sxs-lookup"><span data-stu-id="1b24e-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1b24e-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1b24e-105">Suggestion</span></span>

<span data-ttu-id="1b24e-106">W niektórych przypadkach zmniejszenie właściwości PageHeight elementu wyświetlanego przez jedną może przywrócić poprzednią liczbę wyświetlanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="1b24e-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="1b24e-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1b24e-107">Name</span></span>    | <span data-ttu-id="1b24e-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="1b24e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b24e-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="1b24e-109">Scope</span></span>   |<span data-ttu-id="1b24e-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="1b24e-110">Edge</span></span>|
|<span data-ttu-id="1b24e-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="1b24e-111">Version</span></span>|<span data-ttu-id="1b24e-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1b24e-112">4.5</span></span>|
|<span data-ttu-id="1b24e-113">Typ</span><span class="sxs-lookup"><span data-stu-id="1b24e-113">Type</span></span>|<span data-ttu-id="1b24e-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1b24e-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b24e-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1b24e-115">Affected APIs</span></span>

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
