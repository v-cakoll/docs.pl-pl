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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015971"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="3226a-102">Błędy czasu projektowania w Projektant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3226a-102">Design-time errors in the Windows Forms Designer</span></span>

<span data-ttu-id="3226a-103">W tym temacie wyjaśniono znaczenie i użycie listy błędów czasu projektowania, która pojawia się w programie Visual Studio w przypadku niepowodzenia załadowania Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3226a-103">This topic explains the meaning and use of the design-time error list that appears in Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="3226a-104">Jeśli zostanie wyświetlona lista błędów, nie należy interpretować jej jako usterki w projektancie, ale jako pomoc w rozwiązywaniu błędów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3226a-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>

<span data-ttu-id="3226a-105">Podstawowe informacje o tej liście błędów ułatwią debugowanie aplikacji przez podanie szczegółowych informacji o błędach i sugerowanie możliwych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="3226a-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>

## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="3226a-106">Interfejs listy błędów czasu projektowania</span><span class="sxs-lookup"><span data-stu-id="3226a-106">The design-time error list interface</span></span>

<span data-ttu-id="3226a-107">Jeśli nie można załadować Projektant formularzy systemu Windows, w projektancie pojawi się lista błędów.</span><span class="sxs-lookup"><span data-stu-id="3226a-107">If the Windows Forms Designer fails to load, an error list appears in the designer.</span></span> <span data-ttu-id="3226a-108">Błędy są pogrupowane w kategorie.</span><span class="sxs-lookup"><span data-stu-id="3226a-108">The errors are grouped into categories.</span></span> <span data-ttu-id="3226a-109">Na przykład jeśli masz cztery wystąpienia niezadeklarowanych zmiennych, zostaną one pogrupowane w tej samej kategorii błędów.</span><span class="sxs-lookup"><span data-stu-id="3226a-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="3226a-110">Każda kategoria błędów zawiera krótki opis podsumowujący błąd.</span><span class="sxs-lookup"><span data-stu-id="3226a-110">Each error category includes a brief description that summarizes the error.</span></span>

<span data-ttu-id="3226a-111">Kategorię błędów można rozwinąć lub zwinąć, klikając nagłówek kategorii błędów lub klikając przycisk Rozwiń/Zwiń Pagon.</span><span class="sxs-lookup"><span data-stu-id="3226a-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="3226a-112">Po rozwinięciu kategorii błędów zostanie wyświetlona następująca dodatkowa pomoc:</span><span class="sxs-lookup"><span data-stu-id="3226a-112">When you expand an error category, the following additional help is displayed:</span></span>

- <span data-ttu-id="3226a-113">Wystąpienia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="3226a-113">Instances of this error.</span></span>

- <span data-ttu-id="3226a-114">Pomoc dotycząca tego błędu.</span><span class="sxs-lookup"><span data-stu-id="3226a-114">Help with this error.</span></span>

- <span data-ttu-id="3226a-115">Wpisy na forum dotyczące tego błędu.</span><span class="sxs-lookup"><span data-stu-id="3226a-115">Forum posts about this error.</span></span>

### <a name="instances-of-this-error"></a><span data-ttu-id="3226a-116">Wystąpienia tego błędu</span><span class="sxs-lookup"><span data-stu-id="3226a-116">Instances of this error</span></span>

<span data-ttu-id="3226a-117">Dodatkowa pomoc dla wszystkich wystąpień błędu w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="3226a-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="3226a-118">Wiele błędów zawiera dokładną lokalizację w następującym formacie: *[nazwa projektu]* *[nazwa formularza]* wiersz: *[numer wiersza]* kolumna: *[numer kolumny]* .</span><span class="sxs-lookup"><span data-stu-id="3226a-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="3226a-119">Link **Przejdź do kodu** przenosi do lokalizacji w kodzie, w której występuje błąd.</span><span class="sxs-lookup"><span data-stu-id="3226a-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>

<span data-ttu-id="3226a-120">Jeśli stos wywołań jest skojarzony z błędem, można kliknąć link **Pokaż stos wywołań** , który dodatkowo rozszerza błąd w celu wyświetlenia stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="3226a-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="3226a-121">Badanie stosu może zapewnić cenne informacje debugowania.</span><span class="sxs-lookup"><span data-stu-id="3226a-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="3226a-122">Można na przykład śledzić funkcje, które zostały wywołane przed wystąpieniem błędu.</span><span class="sxs-lookup"><span data-stu-id="3226a-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="3226a-123">Stos wywołań jest wybierany, aby można go było skopiować i zapisać.</span><span class="sxs-lookup"><span data-stu-id="3226a-123">The call stack is selectable so that you can copy and save it.</span></span>

> [!NOTE]
> <span data-ttu-id="3226a-124">W Visual Basic Lista błędów czasu projektowania nie wyświetla więcej niż jednego błędu, ale może wyświetlić wiele wystąpień tego samego błędu.</span><span class="sxs-lookup"><span data-stu-id="3226a-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="3226a-125">W wizualizacji C++błędy nie mają linków do kodu linków/numerów wierszy.</span><span class="sxs-lookup"><span data-stu-id="3226a-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>

### <a name="forum-posts-about-this-error"></a><span data-ttu-id="3226a-126">Wpisy na forum dotyczące tego błędu</span><span class="sxs-lookup"><span data-stu-id="3226a-126">Forum posts about this error</span></span>

<span data-ttu-id="3226a-127">Dodatkowa pomoc zawiera link do wpisów na forum związanych z błędem.</span><span class="sxs-lookup"><span data-stu-id="3226a-127">The additional help includes a link to forum posts related to the error.</span></span> <span data-ttu-id="3226a-128">Fora są przeszukiwane w oparciu o ciąg komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="3226a-128">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="3226a-129">Możesz również spróbować wyszukać na następujących forach:</span><span class="sxs-lookup"><span data-stu-id="3226a-129">You can also try searching on the following forums:</span></span>

- [<span data-ttu-id="3226a-130">Forum Projektant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3226a-130">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [<span data-ttu-id="3226a-131">Forum Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3226a-131">Windows Forms forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a><span data-ttu-id="3226a-132">Ignoruj i Kontynuuj</span><span class="sxs-lookup"><span data-stu-id="3226a-132">Ignore and continue</span></span>

<span data-ttu-id="3226a-133">Można zignorować warunek błędu i kontynuować ładowanie projektanta.</span><span class="sxs-lookup"><span data-stu-id="3226a-133">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="3226a-134">Wybranie tej akcji może spowodować nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="3226a-134">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="3226a-135">Na przykład kontrolki mogą nie być wyświetlane na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="3226a-135">For example, controls may not appear on the design surface.</span></span>

## <a name="see-also"></a><span data-ttu-id="3226a-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3226a-136">See also</span></span>

- <span data-ttu-id="3226a-137">[Rozwiązywanie problemów związanych z projektowaniem czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="3226a-137">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
- [<span data-ttu-id="3226a-138">Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników</span><span class="sxs-lookup"><span data-stu-id="3226a-138">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="3226a-139">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="3226a-139">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="3226a-140">[Projektant formularzy systemu Windows komunikaty o błędach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3226a-140">[Windows Forms Designer Error Messages](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span></span>
