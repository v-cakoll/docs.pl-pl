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
ms.openlocfilehash: 40322dc6c5facd4167a4c9ac5c12fdf2a8831b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526456"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="54efd-102">Najlepsze praktyki dotyczące formantu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="54efd-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="54efd-103"><xref:System.Windows.Forms.TableLayoutPanel> Kontrola zapewnia układu zaawansowane funkcje, które należy rozważyć przed użyciem na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="54efd-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="54efd-104">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="54efd-104">Recommendations</span></span>  
 <span data-ttu-id="54efd-105">Poniższe zalecenia pomogą użyj <xref:System.Windows.Forms.TableLayoutPanel> formantu, aby jego najważniejsze korzyści.</span><span class="sxs-lookup"><span data-stu-id="54efd-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="54efd-106">Użyj docelowych</span><span class="sxs-lookup"><span data-stu-id="54efd-106">Targeted Use</span></span>  
 <span data-ttu-id="54efd-107">Użyj <xref:System.Windows.Forms.TableLayoutPanel> kontrolować oszczędnie.</span><span class="sxs-lookup"><span data-stu-id="54efd-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="54efd-108">W sytuacjach wszystkie, które wymagają układu o zmiennym rozmiarze nie należy używać go.</span><span class="sxs-lookup"><span data-stu-id="54efd-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="54efd-109">Poniższa lista zawiera opis układy, korzystają najbardziej z użycia <xref:System.Windows.Forms.TableLayoutPanel> sterowania:</span><span class="sxs-lookup"><span data-stu-id="54efd-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="54efd-110">Układy, w których istnieje wiele części formularza, które proporcjonalnie do siebie.</span><span class="sxs-lookup"><span data-stu-id="54efd-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="54efd-111">Układy, które zostaną zmodyfikowane lub generowane dynamicznie w czasie wykonywania, takie jak formularze wprowadzania danych, których można dostosowywać użytkownika pola dodane lub usunięte zgodnie z preferencjami.</span><span class="sxs-lookup"><span data-stu-id="54efd-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="54efd-112">Układy, które powinny pozostać w ogólnej stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="54efd-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="54efd-113">Na przykład może być okno dialogowe, które powinny pozostać mniejsza niż 800 x 600, ale należy do obsługi zlokalizowanych ciągów.</span><span class="sxs-lookup"><span data-stu-id="54efd-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="54efd-114">Poniższa lista zawiera opis układy nie znacznie korzyści ze stosowania <xref:System.Windows.Forms.TableLayoutPanel> sterowania:</span><span class="sxs-lookup"><span data-stu-id="54efd-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="54efd-115">Proste formularze wprowadzania danych z jedną kolumną etykiety i pojedynczej kolumny obszarów wprowadzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="54efd-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="54efd-116">Formularze za pomocą jednej dużych wyświetlić obszar, który powinien wypełnił dostępne miejsce podczas zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="54efd-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="54efd-117">Na przykład jest formularz, który wyświetla pojedynczy <xref:System.Windows.Forms.PropertyGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="54efd-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="54efd-118">Zakotwiczanie, użyj w tym przypadku, ponieważ nic rozszerzyć gdy zmieniany jest rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="54efd-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="54efd-119">Wybierz uważnie, które kontrolki musi być <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="54efd-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="54efd-120">Jeśli dysponujesz miejscem na tekst zwiększa się o 30% przy użyciu Zakotwiczanie, rozważ użycie <xref:System.Windows.Forms.Control.Anchor%2A> tylko właściwości.</span><span class="sxs-lookup"><span data-stu-id="54efd-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="54efd-121">Jeśli można oszacować miejsca wymaganego przez układ, użycie <xref:System.Windows.Forms.Control.Dock%2A> i <xref:System.Windows.Forms.Control.Anchor%2A> jest łatwiejsze niż Szacowanie szczegóły pozostałego miejsca i <xref:System.Windows.Forms.Control.AutoSize%2A> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="54efd-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="54efd-122">Na ogół podczas projektowania układu z <xref:System.Windows.Forms.TableLayoutPanel> kontrolować, projekt powinien być tak proste, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="54efd-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="54efd-123">Okno konspektu dokumentu</span><span class="sxs-lookup"><span data-stu-id="54efd-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="54efd-124">Okno konspektu dokumentu umożliwia układu, która służy do manipulowania relacje porządek i nadrzędny podrzędny dla Twoich formantów w widoku drzewa.</span><span class="sxs-lookup"><span data-stu-id="54efd-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="54efd-125">Z **menu Widok**, wybierz pozycję **inne okna**, a następnie wybierz pozycję **konspekt dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="54efd-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="54efd-126">Unikaj zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="54efd-126">Avoid Nesting</span></span>  
 <span data-ttu-id="54efd-127">Unikaj zagnieżdżanie innych <xref:System.Windows.Forms.TableLayoutPanel> steruje w obrębie <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="54efd-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="54efd-128">Debugowanie zagnieżdżonych układów może być trudne.</span><span class="sxs-lookup"><span data-stu-id="54efd-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="54efd-129">Unikaj dziedziczenie Visual</span><span class="sxs-lookup"><span data-stu-id="54efd-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="54efd-130"><xref:System.Windows.Forms.TableLayoutPanel> Formant nie obsługuje dziedziczenia visual w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="54efd-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="54efd-131">A <xref:System.Windows.Forms.TableLayoutPanel> kontroli w klasie pochodnej pojawia się jako "zablokowana" w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="54efd-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54efd-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54efd-132">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
