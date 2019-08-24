---
title: 'Instrukcje: kontrolki autoryzacji dla formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45a6ae68102204ad8506027065c2676e02fdd7a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015918"
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="1de6f-102">Instrukcje: Kontrolki autora dla Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1de6f-102">How to: Author controls for Windows Forms</span></span>

<span data-ttu-id="1de6f-103">Kontrolka reprezentuje graficzny link między użytkownikiem a programem.</span><span class="sxs-lookup"><span data-stu-id="1de6f-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="1de6f-104">Kontrolka może udostępniać lub przetwarzać dane, akceptować wprowadzanie danych przez użytkownika, odpowiadać na zdarzenia lub wykonywać dowolną liczbę innych funkcji, które łączą użytkownika i aplikację.</span><span class="sxs-lookup"><span data-stu-id="1de6f-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="1de6f-105">Ponieważ kontrolka jest zasadniczo składnikiem interfejsu graficznego, może służyć dowolnej funkcji, która robi składnik, a także zapewnia interakcję z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="1de6f-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="1de6f-106">Formanty są tworzone w celu obsłużenia określonych celów, a formanty tworzenia są po prostu innym zadaniem programistycznym.</span><span class="sxs-lookup"><span data-stu-id="1de6f-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="1de6f-107">Z tego względu poniższe kroki przedstawiają przegląd procesu tworzenia kontroli.</span><span class="sxs-lookup"><span data-stu-id="1de6f-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="1de6f-108">Linki zawierają dodatkowe informacje dotyczące poszczególnych kroków.</span><span class="sxs-lookup"><span data-stu-id="1de6f-108">Links provide additional information on the individual steps.</span></span>

## <a name="to-author-a-control"></a><span data-ttu-id="1de6f-109">Aby utworzyć kontrolkę</span><span class="sxs-lookup"><span data-stu-id="1de6f-109">To author a control</span></span>

1. <span data-ttu-id="1de6f-110">Określ, co ma być wykonywane przez formant, lub część, która będzie odtwarzana w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1de6f-110">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="1de6f-111">Czynniki, które należy wziąć pod uwagę:</span><span class="sxs-lookup"><span data-stu-id="1de6f-111">Factors to consider are:</span></span>

    - <span data-ttu-id="1de6f-112">Jakiego rodzaju interfejsu graficznego potrzebujesz?</span><span class="sxs-lookup"><span data-stu-id="1de6f-112">What kind of graphical interface do you need?</span></span>

    - <span data-ttu-id="1de6f-113">Jakie Interakcje użytkownika będą obsługiwane przez tę kontrolkę?</span><span class="sxs-lookup"><span data-stu-id="1de6f-113">What specific user interactions will this control handle?</span></span>

    - <span data-ttu-id="1de6f-114">Czy wymagane funkcje są dostępne w ramach istniejących kontrolek?</span><span class="sxs-lookup"><span data-stu-id="1de6f-114">Is the functionality you need provided by any existing controls?</span></span>

    - <span data-ttu-id="1de6f-115">Czy możesz uzyskać dostęp do potrzebnych funkcji, łącząc kilka Windows Forms formantów?</span><span class="sxs-lookup"><span data-stu-id="1de6f-115">Can you get the functionality you need by combining several Windows Forms controls?</span></span>

2. <span data-ttu-id="1de6f-116">Jeśli potrzebujesz modelu obiektowego dla kontrolki, określ, w jaki sposób funkcje będą dystrybuowane w całym modelu obiektów, i Podziel się funkcjonalnością między kontrolką a podobiektami.</span><span class="sxs-lookup"><span data-stu-id="1de6f-116">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="1de6f-117">Model obiektu może być przydatny, jeśli planujesz kontrolę złożoną lub chcesz dołączyć kilka funkcji.</span><span class="sxs-lookup"><span data-stu-id="1de6f-117">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>

3. <span data-ttu-id="1de6f-118">Określ typ formantu (na przykład kontrolka użytkownika, kontrolka niestandardowa, dziedziczona Windows Forms kontrolki).</span><span class="sxs-lookup"><span data-stu-id="1de6f-118">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="1de6f-119">Aby uzyskać szczegółowe informacje, zobacz [zalecenia dotyczące typu kontroli](control-type-recommendations.md) i różne [rodzaje kontrolek niestandardowych](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1de6f-119">For details, see [Control Type Recommendations](control-type-recommendations.md) and [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

4. <span data-ttu-id="1de6f-120">Funkcje ekspresowe jako właściwości, metody i zdarzenia kontrolki i jej podobiektów lub struktur oddziałów, a także Przypisz odpowiednie poziomy dostępu (na przykład publiczne, chronione itd.).</span><span class="sxs-lookup"><span data-stu-id="1de6f-120">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>

5. <span data-ttu-id="1de6f-121">Jeśli potrzebujesz niestandardowego rysowania kontrolki, Dodaj do niej kod.</span><span class="sxs-lookup"><span data-stu-id="1de6f-121">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="1de6f-122">Aby uzyskać szczegółowe informacje, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="1de6f-122">For details, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

6. <span data-ttu-id="1de6f-123">Jeśli formant dziedziczy z <xref:System.Windows.Forms.UserControl>, można przetestować jego zachowanie w czasie wykonywania przez skompilowanie projektu kontrolki i uruchomienie go w **kontenerze testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="1de6f-123">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="1de6f-124">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1de6f-124">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

7. <span data-ttu-id="1de6f-125">Możesz również testować i debugować kontrolkę, tworząc nowy projekt, taki jak aplikacja systemu Windows i umieszczając go w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="1de6f-125">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="1de6f-126">Ten proces jest przedstawiany jako część [przewodnika: Tworzenie złożonego formantu](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="1de6f-126">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span></span>

8. <span data-ttu-id="1de6f-127">Podczas dodawania każdej funkcji Dodaj funkcje do projektu testowego, aby skorzystać z nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="1de6f-127">As you add each feature, add features to your test project to exercise the new functionality.</span></span>

9. <span data-ttu-id="1de6f-128">Powtórz tę czynność, aby udoskonalić projekt.</span><span class="sxs-lookup"><span data-stu-id="1de6f-128">Repeat, refining the design.</span></span>

10. <span data-ttu-id="1de6f-129">Spakuj i Wdróż swój formant.</span><span class="sxs-lookup"><span data-stu-id="1de6f-129">Package and deploy your control.</span></span> <span data-ttu-id="1de6f-130">Aby uzyskać szczegółowe informacje, zobacz [pierwsze spojrzenie na wdrożenie w programie Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span><span class="sxs-lookup"><span data-stu-id="1de6f-130">For details, see [First look at deployment in Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span></span>

## <a name="see-also"></a><span data-ttu-id="1de6f-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1de6f-131">See also</span></span>

- [<span data-ttu-id="1de6f-132">Instrukcje: Dziedzicz z klasy UserControl</span><span class="sxs-lookup"><span data-stu-id="1de6f-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="1de6f-133">Instrukcje: Dziedzicz z klasy kontrolki</span><span class="sxs-lookup"><span data-stu-id="1de6f-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="1de6f-134">Instrukcje: Dziedzicz z istniejących kontrolek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1de6f-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="1de6f-135">Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="1de6f-135">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="1de6f-136">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="1de6f-136">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
