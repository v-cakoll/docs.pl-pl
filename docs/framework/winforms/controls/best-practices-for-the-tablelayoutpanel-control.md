---
title: Najlepsze praktyki dotyczące formantu TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 6be6d0904d5b52e5188f0a5a16aaefa08265379c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674196"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="43786-102">Najlepsze praktyki dotyczące formantu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="43786-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="43786-103"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli udostępnia funkcje zaawansowane układu, które należy rozważyć przed użyciem na formularzach Windows.</span><span class="sxs-lookup"><span data-stu-id="43786-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="43786-104">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="43786-104">Recommendations</span></span>  
 <span data-ttu-id="43786-105">Poniższe zalecenia ułatwi użycie <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do jej zaletą najlepsze.</span><span class="sxs-lookup"><span data-stu-id="43786-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="43786-106">Użyj docelowego</span><span class="sxs-lookup"><span data-stu-id="43786-106">Targeted Use</span></span>  
 <span data-ttu-id="43786-107">Użyj <xref:System.Windows.Forms.TableLayoutPanel> kontrolować rzadko.</span><span class="sxs-lookup"><span data-stu-id="43786-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="43786-108">We wszystkich sytuacjach wymagających o zmiennym rozmiarze układu nie należy używać go.</span><span class="sxs-lookup"><span data-stu-id="43786-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="43786-109">Na poniższej liście opisano układy, korzystają najbardziej z użycia zestawów <xref:System.Windows.Forms.TableLayoutPanel> sterowania:</span><span class="sxs-lookup"><span data-stu-id="43786-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="43786-110">Układy, w których istnieje wiele części formularza, które proporcjonalnie do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="43786-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="43786-111">Układy zostanie zmodyfikowany lub generowany dynamicznie w czasie wykonywania, takich jak formularze wprowadzania danych, które mają pól możliwych do dostosowania użytkownika dodawane lub odejmowane na podstawie preferencji.</span><span class="sxs-lookup"><span data-stu-id="43786-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="43786-112">Układy, które powinny pozostać w ogólnej o stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="43786-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="43786-113">Na przykład masz okno dialogowe, które powinny pozostać mniejsza niż 800 x 600, ale trzeba obsługiwać zlokalizowane ciągi.</span><span class="sxs-lookup"><span data-stu-id="43786-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="43786-114">Na poniższej liście opisano układy nie osiągają znaczne korzyści z używania <xref:System.Windows.Forms.TableLayoutPanel> sterowania:</span><span class="sxs-lookup"><span data-stu-id="43786-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="43786-115">Proste formularze wprowadzania danych z jedną kolumną etykiet i jedną kolumnę obszarów wprowadzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="43786-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="43786-116">Formularze za pomocą pojedynczego dużych wyświetlać obszar, który należy wypełnić całe dostępne miejsce po wystąpieniu zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="43786-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="43786-117">Na przykład jest formularz, który wyświetla jedną <xref:System.Windows.Forms.PropertyGrid> kontroli.</span><span class="sxs-lookup"><span data-stu-id="43786-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="43786-118">Zakotwiczanie, użyj w tym przypadku ponieważ nic powinni rozwinąć pozycję gdy zmieniany jest rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="43786-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="43786-119">Wybierz uważnie, które kontrolki, które muszą być w <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="43786-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="43786-120">Jeśli dysponujesz miejscem na tekście rośnie o 30%, za pomocą Zakotwiczanie, rozważ użycie <xref:System.Windows.Forms.Control.Anchor%2A> tylko właściwości.</span><span class="sxs-lookup"><span data-stu-id="43786-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="43786-121">Jeśli miejsce wymagane przez układ można oszacować, użyj <xref:System.Windows.Forms.Control.Dock%2A> i <xref:System.Windows.Forms.Control.Anchor%2A> jest łatwiejsze niż szacowania szczegóły ilość wolnego miejsca i <xref:System.Windows.Forms.Control.AutoSize%2A> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="43786-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="43786-122">Ogólnie rzecz biorąc, podczas projektowania układu z <xref:System.Windows.Forms.TableLayoutPanel> sterowania, projekt powinien być tak proste, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="43786-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="43786-123">Okno konspektu dokumentu</span><span class="sxs-lookup"><span data-stu-id="43786-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="43786-124">Okno konspektu dokumentu zapewnia układu można używać do manipulowania relacji porządek i nadrzędny podrzędny, dla Twoich kontrolek w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="43786-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="43786-125">Z **menu Widok**, wybierz opcję **Windows inne**, a następnie wybierz **konspekt dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="43786-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="43786-126">Uniknąć zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="43786-126">Avoid Nesting</span></span>  
 <span data-ttu-id="43786-127">Należy unikać zagnieżdżanie innych <xref:System.Windows.Forms.TableLayoutPanel> kontrolki w ramach <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="43786-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="43786-128">Debugowanie układy zagnieżdżonych może być trudne.</span><span class="sxs-lookup"><span data-stu-id="43786-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="43786-129">Należy unikać dziedziczenie Visual</span><span class="sxs-lookup"><span data-stu-id="43786-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="43786-130"><xref:System.Windows.Forms.TableLayoutPanel> Formant nie obsługuje dziedziczenie visual w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="43786-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="43786-131">A <xref:System.Windows.Forms.TableLayoutPanel> formantu w klasie pochodnej pojawia się jako "zablokowany" w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="43786-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43786-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43786-132">See also</span></span>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
