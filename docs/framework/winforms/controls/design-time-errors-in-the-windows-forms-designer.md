---
title: Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: 7ee4ce1d6efdc4927fc2d20100f0b12f7405261f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213145"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="0f92e-102">Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0f92e-102">Design-Time Errors in the Windows Forms Designer</span></span>
<span data-ttu-id="0f92e-103">W tym temacie wyjaśniono znaczenie i użycie listy błędów podczas projektowania, który pojawia się w programie Microsoft Visual Studio, gdy Windows Forms Designer nie można załadować.</span><span class="sxs-lookup"><span data-stu-id="0f92e-103">This topic explains the meaning and use of the design-time error list that appears in Microsoft Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="0f92e-104">Jeśli zostanie wyświetlona lista ten błąd, należy nie ich interpretacji jako błąd w projektancie, ale także jako pomoc do poprawiania błędów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0f92e-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>  
  
 <span data-ttu-id="0f92e-105">Podstawową wiedzę na temat tej listy błędów są pomocne podczas debugowania aplikacji, zapewniając szczegółowe informacje na temat błędów i sugerowanie możliwych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="0f92e-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>  
  
## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="0f92e-106">Interfejs listę błędów podczas projektowania</span><span class="sxs-lookup"><span data-stu-id="0f92e-106">The Design-Time Error List Interface</span></span>  
 <span data-ttu-id="0f92e-107">W przypadku niepowodzenia można załadować projektanta formularzy Windows w Projektancie pojawi się lista błędów.</span><span class="sxs-lookup"><span data-stu-id="0f92e-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="0f92e-108">Błędy są podzielone na kategorie.</span><span class="sxs-lookup"><span data-stu-id="0f92e-108">The errors are grouped into categories.</span></span> <span data-ttu-id="0f92e-109">Na przykład jeśli cztery wystąpienia niezadeklarowany zmiennych, te są grupowane w tej samej kategorii błędów.</span><span class="sxs-lookup"><span data-stu-id="0f92e-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="0f92e-110">Każda kategoria błędu zawiera krótki opis, który znajduje się podsumowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="0f92e-110">Each error category includes a brief description that summarizes the error.</span></span>  
  
 <span data-ttu-id="0f92e-111">Można rozwinąć lub zwinąć do kategorii błędów, klikając nagłówek kategorii błędów lub przez kliknięcie przycisku cudzysłów ostrokątny rozwijania/zwijania.</span><span class="sxs-lookup"><span data-stu-id="0f92e-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="0f92e-112">Po rozwinięciu do kategorii błędów, zostanie wyświetlony następujący dodatkowej pomocy:</span><span class="sxs-lookup"><span data-stu-id="0f92e-112">When you expand an error category, the following additional help is displayed:</span></span>  
  
-   <span data-ttu-id="0f92e-113">Wystąpienia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="0f92e-113">Instances of this error.</span></span>  
  
-   <span data-ttu-id="0f92e-114">Pomoc dotycząca tego błędu.</span><span class="sxs-lookup"><span data-stu-id="0f92e-114">Help with this error.</span></span>  
  
-   <span data-ttu-id="0f92e-115">Posty na forum dotyczące tego błędu.</span><span class="sxs-lookup"><span data-stu-id="0f92e-115">Forum posts about this error.</span></span>  
  
### <a name="instances-of-this-error"></a><span data-ttu-id="0f92e-116">Wystąpienia tego błędu</span><span class="sxs-lookup"><span data-stu-id="0f92e-116">Instances of This Error</span></span>  
 <span data-ttu-id="0f92e-117">Dodatkową pomoc, listę wszystkich wystąpień błąd w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="0f92e-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="0f92e-118">Wiele błędów obejmują dokładną lokalizację, w następującym formacie: *[Nazwa projektu]* *[nazwa formularza]* wiersza:*[numer wiersza]* kolumny:*— kolumny numer*.</span><span class="sxs-lookup"><span data-stu-id="0f92e-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="0f92e-119">**Przejdź do kodu** link umożliwia przejście do lokalizacji w kodzie, w którym występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="0f92e-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>  
  
 <span data-ttu-id="0f92e-120">Jeśli stos wywołań jest skojarzony z powodu błędu, możesz kliknąć **Pokaż stos wywołań** łącze, które bardziej rozszerza błędu, aby wyświetlić stos wywołań.</span><span class="sxs-lookup"><span data-stu-id="0f92e-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="0f92e-121">Badanie stosu może dostarczyć cennych informacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="0f92e-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="0f92e-122">Na przykład można śledzić funkcje, które zostały wywołane przed wystąpieniem błędu.</span><span class="sxs-lookup"><span data-stu-id="0f92e-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="0f92e-123">Stos wywołań jest możliwy, tak, aby skopiować i zapisać go.</span><span class="sxs-lookup"><span data-stu-id="0f92e-123">The call stack is selectable so that you can copy and save it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f92e-124">W języku Visual Basic na liście błędów podczas projektowania nie są wyświetlane więcej niż jeden błąd, ale mogą być wyświetlane wiele wystąpień tego samego błędu.</span><span class="sxs-lookup"><span data-stu-id="0f92e-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="0f92e-125">W programie Visual C++ błędy nie mają przejdź do kodu łączy/linii numer łącza.</span><span class="sxs-lookup"><span data-stu-id="0f92e-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>  
  
### <a name="help-with-this-error"></a><span data-ttu-id="0f92e-126">Pomoc dotycząca tego błędu</span><span class="sxs-lookup"><span data-stu-id="0f92e-126">Help with This Error</span></span>  
 <span data-ttu-id="0f92e-127">Jeśli błąd zawiera łącze do skojarzonego tematu pomocy MSDN, dodatkowej pomocy zawiera łącze do tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="0f92e-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="0f92e-128">Po kliknięciu łącza, skojarzonego tematu Pomocy pojawia się w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f92e-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>  
  
### <a name="forum-posts-about-this-error"></a><span data-ttu-id="0f92e-129">Posty na forum dotyczące tego błędu</span><span class="sxs-lookup"><span data-stu-id="0f92e-129">Forum posts about this error</span></span>  
 <span data-ttu-id="0f92e-130">Dodatkową pomoc zawiera łącze do wpisy na forum MSDN dotyczące błędu.</span><span class="sxs-lookup"><span data-stu-id="0f92e-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="0f92e-131">Fora są przeszukiwane w oparciu o ciąg komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="0f92e-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="0f92e-132">Możesz też spróbować przeszukiwanie forów następujące:</span><span class="sxs-lookup"><span data-stu-id="0f92e-132">You can also try searching the following forums:</span></span>  
  
-   [<span data-ttu-id="0f92e-133">Forum projektanta programu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f92e-133">Windows Forms Designer Forum</span></span>](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [<span data-ttu-id="0f92e-134">Windows Forms forów</span><span class="sxs-lookup"><span data-stu-id="0f92e-134">Windows Forms Forums</span></span>](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a><span data-ttu-id="0f92e-135">Ignoruj i Kontynuuj</span><span class="sxs-lookup"><span data-stu-id="0f92e-135">Ignore and Continue</span></span>  
 <span data-ttu-id="0f92e-136">Można zignorować warunek błędu i kontynuowania ładowania projektanta.</span><span class="sxs-lookup"><span data-stu-id="0f92e-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="0f92e-137">Wybranie tej akcji może spowodować nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="0f92e-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="0f92e-138">Na przykład formanty nie może występować na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="0f92e-138">For example, controls may not appear on the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f92e-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f92e-139">See also</span></span>

- [<span data-ttu-id="0f92e-140">Rozwiązywanie problemów podczas projektowania</span><span class="sxs-lookup"><span data-stu-id="0f92e-140">Troubleshooting Design-Time Development</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [<span data-ttu-id="0f92e-141">Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów</span><span class="sxs-lookup"><span data-stu-id="0f92e-141">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="0f92e-142">Opracowywanie formantów formularzy systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="0f92e-142">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="0f92e-143">Projektant formularzy systemu Windows — Komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="0f92e-143">Windows Forms Designer Error Messages</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
