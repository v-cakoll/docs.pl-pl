---
title: "Właściwości formantów formularzy systemu Windows obsługujące dostęp — Wytyczne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ca18b35b90b028054e68a0a14fecc819a6c20b9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a><span data-ttu-id="85227-102">Właściwości formantów formularzy systemu Windows obsługujące dostęp — Wytyczne</span><span class="sxs-lookup"><span data-stu-id="85227-102">Properties on Windows Forms Controls That Support Accessibility Guidelines</span></span>
<span data-ttu-id="85227-103">Formanty standardowe przyborniku dla formularzy systemu Windows obsługują wiele wytycznych ułatwień dostępu, w tym udostępnianie fokus klawiatury i udostępnianie elementów ekranu.</span><span class="sxs-lookup"><span data-stu-id="85227-103">Controls on the standard toolbox for Windows Forms support many of the accessibility guidelines, including exposing the keyboard focus and exposing the screen elements.</span></span>  
  
## <a name="planning-ahead-for-accessibility"></a><span data-ttu-id="85227-104">Planowanie wyprzedzeniem ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="85227-104">Planning Ahead for Accessibility</span></span>  
 <span data-ttu-id="85227-105">Właściwości formantów mogą służyć do obsługi innych dostęp — wytyczne, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="85227-105">The controls' properties can be used to support other accessibility guidelines as shown in the following table.</span></span> <span data-ttu-id="85227-106">Ponadto należy używać menu, aby zapewnić dostęp do funkcji programu.</span><span class="sxs-lookup"><span data-stu-id="85227-106">Additionally, you should use menus to provide access to program features.</span></span>  
  
|<span data-ttu-id="85227-107">Właściwość formantu</span><span class="sxs-lookup"><span data-stu-id="85227-107">Control Property</span></span>|<span data-ttu-id="85227-108">Zagadnienia dotyczące ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="85227-108">Considerations for Accessibility</span></span>|  
|----------------------|--------------------------------------|  
|<span data-ttu-id="85227-109">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="85227-109">AccessibleDescription</span></span>|<span data-ttu-id="85227-110">Opis jest zgłaszane do narzędzi ułatwień dostępu, takich jak czytniki ekranu.</span><span class="sxs-lookup"><span data-stu-id="85227-110">The description is reported to accessibility aids such as screen readers.</span></span> <span data-ttu-id="85227-111">Narzędzi ułatwień dostępu są programy specjalistyczne i urządzenia, które pomagają osób niepełnosprawnych komputerów wydajniej wykorzystywać.</span><span class="sxs-lookup"><span data-stu-id="85227-111">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span>|  
|<span data-ttu-id="85227-112">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="85227-112">AccessibleName</span></span>|<span data-ttu-id="85227-113">Nazwa przekazywana do narzędzi ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="85227-113">The name that will be reported to the accessibility aids.</span></span>|  
|<span data-ttu-id="85227-114">AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="85227-114">AccessibleRole</span></span>|<span data-ttu-id="85227-115">Opisuje elementu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="85227-115">Describes the use of the element in the user interface.</span></span>|  
|<span data-ttu-id="85227-116">TabIndex</span><span class="sxs-lookup"><span data-stu-id="85227-116">TabIndex</span></span>|<span data-ttu-id="85227-117">Tworzy ścieżkę nawigacyjną za pośrednictwem za pomocą formularza.</span><span class="sxs-lookup"><span data-stu-id="85227-117">Creates a sensible navigational path through the form.</span></span> <span data-ttu-id="85227-118">Jest ważne dla formantów bez etykiet wewnętrznych, takich jak pola tekstowe, ich skojarzone etykiety poprzedzają w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="85227-118">It is important for controls without intrinsic labels, such as text boxes, to have their associated label immediately precede them in the tab order.</span></span>|  
|<span data-ttu-id="85227-119">Tekst</span><span class="sxs-lookup"><span data-stu-id="85227-119">Text</span></span>|<span data-ttu-id="85227-120">Użyj znaku "&", aby utworzyć klucze dostępu.</span><span class="sxs-lookup"><span data-stu-id="85227-120">Use the "&" character to create access keys.</span></span> <span data-ttu-id="85227-121">Za pomocą klawiszy dostępu jest częścią klawiaturę udokumentowaną dostępowi do funkcji.</span><span class="sxs-lookup"><span data-stu-id="85227-121">Using access keys is part of providing documented keyboard access to features.</span></span>|  
|<span data-ttu-id="85227-122">Rozmiar czcionki</span><span class="sxs-lookup"><span data-stu-id="85227-122">Font Size</span></span>|<span data-ttu-id="85227-123">Jeśli rozmiar czcionki nie jest regulowany, następnie go ustawić punkty 10 lub większą.</span><span class="sxs-lookup"><span data-stu-id="85227-123">If the font size is not adjustable, then it should be set to 10 points or larger.</span></span> <span data-ttu-id="85227-124">Po ustawieniu formularza rozmiar czcionki, wszystkie formanty, które są następnie dodany do formularza będą miały taki sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="85227-124">Once the form's font size is set, all the controls added to the form thereafter will have the same size.</span></span>|  
|<span data-ttu-id="85227-125">ForeColor</span><span class="sxs-lookup"><span data-stu-id="85227-125">Forecolor</span></span>|<span data-ttu-id="85227-126">Jeśli ta właściwość ma ustawioną wartość domyślna, preferencje kolorów dla użytkownika będą używane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="85227-126">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="85227-127">Kolor tła</span><span class="sxs-lookup"><span data-stu-id="85227-127">Backcolor</span></span>|<span data-ttu-id="85227-128">Jeśli ta właściwość ma ustawioną wartość domyślna, preferencje kolorów dla użytkownika będą używane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="85227-128">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="85227-129">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="85227-129">BackgroundImage</span></span>|<span data-ttu-id="85227-130">Pozostaw pole puste, aby zwiększyć czytelność tekstu tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="85227-130">Leave this property blank to make text more readable.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85227-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85227-131">See Also</span></span>  
 [<span data-ttu-id="85227-132">Wskazówki: Tworzenie dostępny aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="85227-132">Walkthrough: Creating an Accessible Windows-based Application</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
