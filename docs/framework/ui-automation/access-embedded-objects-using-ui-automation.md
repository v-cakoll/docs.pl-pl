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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 05f9359aa055019b517abb1b7c86ca386d630e41
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534752"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="e3aaa-102">Uzyskiwanie dostępu do obiektów osadzonych przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e3aaa-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="e3aaa-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e3aaa-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e3aaa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e3aaa-105">W tym temacie przedstawiono sposób [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] może służyć do udostępnienia obiektów osadzonych w zawartości kontrolki tekstu.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3aaa-106">Może zawierać obiekty osadzone, obrazy, hiperłącza, przyciski, tabel lub kontrolki ActiveX.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="e3aaa-107">Osadzone obiekty są traktowane jako elementy podrzędne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="e3aaa-108">Dzięki temu można uwidocznić za pośrednictwem tej samej struktury drzewa automatyzacji interfejsu użytkownika, jak wszystkie inne [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementów.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="e3aaa-109">Funkcje, z kolei jest dostępna za pośrednictwem wzorców kontrolek, zwykle wymagane przez obiekty osadzone typu formantu (na przykład, ponieważ hiperłącza są oparte na tekście zostanie obsługują <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="e3aaa-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="e3aaa-110">![Obiekty osadzone w kontenerze tekstu. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="e3aaa-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="e3aaa-111">Przykładowy dokument z zawartości tekstowej ("czy wiesz?" ...) dwa obiekty i osadzone (obraz whale i hiperłącze tekstowe), używany jako obiekt docelowy dla przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3aaa-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3aaa-112">Example</span></span>  
 <span data-ttu-id="e3aaa-113">Poniższy przykład kodu pokazuje, jak pobrać kolekcję obiektów osadzonych z poziomu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="e3aaa-114">Dla dokumentu próbki, podane we wstępie dwa obiekty będzie zwracany (element obrazu i element tekstowy).</span><span class="sxs-lookup"><span data-stu-id="e3aaa-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3aaa-115">Element obrazu musi zawierać część wewnętrzne tekstu skojarzonych z nim, opisujący obrazu, zazwyczaj w jego <xref:System.Windows.Automation.AutomationElement.NameProperty> (na przykład "niebieski whale.").</span><span class="sxs-lookup"><span data-stu-id="e3aaa-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="e3aaa-116">Jednak po uzyskaniu zakres tekstu, obejmujące obiekt obrazu obrazu ani ten tekst opisu jest zwracany w strumieniu tekstu.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="e3aaa-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3aaa-117">Example</span></span>  
 <span data-ttu-id="e3aaa-118">Poniższy przykład kodu demonstruje sposób uzyskiwania zakres tekstu z obiektu osadzonego w ramach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy tekstu.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="e3aaa-119">Zakres tekstu, pobierane jest pustego zakresu, gdzie następuje początkowy punkt końcowy "...</span><span class="sxs-lookup"><span data-stu-id="e3aaa-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="e3aaa-120">Ocean. (miejsca) "i końcowej punktu końcowego poprzedza zamknięcia". "reprezentujący osadzone hiperłącze (jak to przedstawiono obrazu dostarczonego we wstępie).</span><span class="sxs-lookup"><span data-stu-id="e3aaa-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="e3aaa-121">Nawet jeśli jest to pustego zakresu, nie uważa się zakres wymiaru degeneracji ponieważ ma zakres od zera.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3aaa-122"><xref:System.Windows.Automation.TextPattern> można pobrać oparte na tekście osadzony obiekt na przykład hiperłącze. jednak pomocniczy <xref:System.Windows.Automation.TextPattern> musi pochodzić z osadzonego obiektu do udostępnienia pełną funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="e3aaa-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="e3aaa-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3aaa-123">See Also</span></span>  
 [<span data-ttu-id="e3aaa-124">Przegląd automatyzacji interfejsu użytkownika — TextPattern</span><span class="sxs-lookup"><span data-stu-id="e3aaa-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="e3aaa-125">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="e3aaa-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="e3aaa-126">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="e3aaa-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="e3aaa-127">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e3aaa-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="e3aaa-128">Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e3aaa-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
