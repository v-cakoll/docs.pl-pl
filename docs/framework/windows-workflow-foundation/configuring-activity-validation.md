---
title: Konfigurowanie walidacji działania
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 65928de1dc8b8d9914648463a136790c7978f53c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774182"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="209c4-102">Konfigurowanie walidacji działania</span><span class="sxs-lookup"><span data-stu-id="209c4-102">Configuring Activity Validation</span></span>
<span data-ttu-id="209c4-103">Działanie sprawdzania poprawności umożliwia działanie autorzy i użytkowników zidentyfikować i raportowania błędów w konfiguracji działanie przed jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="209c4-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="209c4-104">Windows Workflow Foundation (WF) udostępnia następujące trzy typy walidacji działania:</span><span class="sxs-lookup"><span data-stu-id="209c4-104">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="209c4-105">`RequiredArgument` i `OverloadGroup` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="209c4-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="209c4-106">Imperatywne sprawdzanie poprawności opartego na kodzie.</span><span class="sxs-lookup"><span data-stu-id="209c4-106">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="209c4-107">Ograniczenia deklaratywne.</span><span class="sxs-lookup"><span data-stu-id="209c4-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="209c4-108">`RequiredArgument` i `OverloadGroup` atrybuty wskazać, że niektóre argumenty w ramach działania są wymagane.</span><span class="sxs-lookup"><span data-stu-id="209c4-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="209c4-109">Imperatywne sprawdzanie poprawności, które są oparte na kodzie zapewnia prostą metodę dla działania w celu udostępnienia weryfikacji o sobie i ograniczenia deklaratywne włączyć weryfikację o aktywności i jej relacji z zawierającego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="209c4-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="209c4-110">Jeśli działanie nie jest prawidłowo skonfigurowany zgodnie z wymaganiami sprawdzania poprawności, zwracane są błędy i ostrzeżenia walidacji.</span><span class="sxs-lookup"><span data-stu-id="209c4-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="209c4-111">Jeśli zawierającego przepływu pracy zostało utworzone za pomocą projektanta przepływów pracy, wszelkie błędy sprawdzania poprawności i ostrzeżenia są wyświetlane w projektancie.</span><span class="sxs-lookup"><span data-stu-id="209c4-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="209c4-112">Jeśli przepływ pracy został utworzony poza projektanta przepływów pracy wszelkie błędy sprawdzania poprawności są zwracane, gdy przepływ pracy zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="209c4-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="209c4-113">Niezależnie od tego, jak przepływ pracy został utworzony przepływ pracy o błędy sprawdzania poprawności nigdy nie może być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="209c4-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="209c4-114">Ta sekcja zawiera omówienie tego rodzaju sprawdzania poprawności działania i jak działanie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="209c4-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="209c4-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="209c4-115">In This Section</span></span>  
 [<span data-ttu-id="209c4-116">Wymagane argumenty i grupy metod przeciążonych</span><span class="sxs-lookup"><span data-stu-id="209c4-116">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="209c4-117">Opisuje sposób używania `RequiredArgument` i `OverloadGroup` atrybutów w celu udostępnienia weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="209c4-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="209c4-118">Walidacja oparta na kodzie imperatywnym</span><span class="sxs-lookup"><span data-stu-id="209c4-118">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="209c4-119">Opisuje sposób używania weryfikacji oparte na kodzie <xref:System.Activities.CodeActivity> i <xref:System.Activities.NativeActivity> na podstawie działania.</span><span class="sxs-lookup"><span data-stu-id="209c4-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="209c4-120">Ograniczenia deklaratywne</span><span class="sxs-lookup"><span data-stu-id="209c4-120">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="209c4-121">Opisuje sposób używania ograniczenia deklaratywne w celu udostępnienia weryfikacji złożone działania.</span><span class="sxs-lookup"><span data-stu-id="209c4-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="209c4-122">Wywoływanie walidacji działania</span><span class="sxs-lookup"><span data-stu-id="209c4-122">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="209c4-123">W tym artykule omówiono podczas walidacji działania jest wywoływane automatycznie oraz sposób jawnego wywołania sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="209c4-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="209c4-124">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="209c4-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="209c4-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="209c4-125">Related Sections</span></span>
