---
title: Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 75c63360eab2cde95698bdaded5c5249a3ca89fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447272"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="cc980-102">Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc980-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="cc980-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="cc980-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cc980-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="cc980-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cc980-105">W tym temacie pokazano, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] mogą być używane do ujawniania obiektów osadzonych w zawartości kontrolki tekstu.</span><span class="sxs-lookup"><span data-stu-id="cc980-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc980-106">Obiekty osadzone mogą zawierać obrazy, hiperłącza, przyciski, tabele lub kontrolki ActiveX.</span><span class="sxs-lookup"><span data-stu-id="cc980-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="cc980-107">Obiekty osadzone są uważane za elementy podrzędne dostawcy tekstu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc980-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="cc980-108">Umożliwia to udostępnienie ich za pomocą tej samej struktury drzewa automatyzacji interfejsu użytkownika co wszystkie inne elementy [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc980-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="cc980-109">Z kolei funkcje są udostępniane za pośrednictwem wzorców formantów zwykle wymaganych przez typ formantu obiektów osadzonych (na przykład, ponieważ hiperłącza są oparte na tekstach, które będą obsługiwać <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="cc980-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="cc980-110">![Obiekty osadzone w kontenerze tekstu.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="cc980-110">![Embedded objects in a text container.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="cc980-111">Przykładowy dokument z zawartością tekstową ("Czy wiesz?" ...) i dwa osadzone obiekty (obraz Whale i Hiperłącze tekstowe) używane jako element docelowy dla przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="cc980-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc980-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc980-112">Example</span></span>  
 <span data-ttu-id="cc980-113">Poniższy przykład kodu demonstruje sposób pobierania kolekcji obiektów osadzonych z poziomu dostawcy tekstu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc980-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="cc980-114">W przypadku przykładowego dokumentu dostarczonego we wprowadzeniu zostaną zwrócone dwa obiekty (element obrazu i element tekstowy).</span><span class="sxs-lookup"><span data-stu-id="cc980-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc980-115">Do elementu obrazu powinien być skojarzony jakiś wewnętrzny tekst, który zawiera opis obrazu, zazwyczaj w <xref:System.Windows.Automation.AutomationElement.NameProperty> (na przykład "niebieska Whale.").</span><span class="sxs-lookup"><span data-stu-id="cc980-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="cc980-116">Jednak gdy zostanie uzyskany zakres tekstu obejmujący obiekt obrazu, w strumieniu tekstowym nie jest zwracany ani obraz, ani ten tekst opisujący.</span><span class="sxs-lookup"><span data-stu-id="cc980-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="cc980-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc980-117">Example</span></span>  
 <span data-ttu-id="cc980-118">Poniższy przykład kodu demonstruje, jak uzyskać zakres tekstu z osadzonego obiektu w ramach dostawcy tekstu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc980-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="cc980-119">Pobrany zakres tekstu jest pustym zakresem, w którym znajduje się początkowy punkt końcowy "...</span><span class="sxs-lookup"><span data-stu-id="cc980-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="cc980-120">utworzeniu. (Space) ", a końcowy koniec poprzedza nawias". "reprezentujący osadzone hiperłącze (jak pokazano w obrazie podanym we wprowadzeniu).</span><span class="sxs-lookup"><span data-stu-id="cc980-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="cc980-121">Mimo że jest to pusty zakres, nie jest uważany za wygenerowanego zakresu, ponieważ jego zakres jest różny od zera.</span><span class="sxs-lookup"><span data-stu-id="cc980-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc980-122"><xref:System.Windows.Automation.TextPattern> może pobrać obiekt osadzony tekstowy, taki jak hiperłącze; jednak pomocnicza <xref:System.Windows.Automation.TextPattern> będzie musiała zostać uzyskana z osadzonego obiektu, aby uwidocznić jej pełną funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="cc980-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="cc980-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc980-123">See also</span></span>

- [<span data-ttu-id="cc980-124">Przegląd automatyzacji interfejsu użytkownika — TextPattern</span><span class="sxs-lookup"><span data-stu-id="cc980-124">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="cc980-125">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="cc980-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="cc980-126">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="cc980-126">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="cc980-127">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc980-127">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="cc980-128">Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc980-128">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
