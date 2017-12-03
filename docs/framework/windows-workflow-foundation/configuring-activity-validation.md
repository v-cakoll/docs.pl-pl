---
title: "Konfigurowanie sprawdzania poprawności działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 440f3ee85fe24707c6bb433736bf6104d9e0dfc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="c46b2-102">Konfigurowanie sprawdzania poprawności działania</span><span class="sxs-lookup"><span data-stu-id="c46b2-102">Configuring Activity Validation</span></span>
<span data-ttu-id="c46b2-103">Działanie sprawdzania poprawności umożliwia autorów działania i użytkowników zidentyfikować i raportów o błędach w konfiguracji działania przed jego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c46b2-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="c46b2-104">udostępnia następujące trzy typy sprawdzania poprawności działania:</span><span class="sxs-lookup"><span data-stu-id="c46b2-104"> provides the following three types of activity validation:</span></span>  
  
-   <span data-ttu-id="c46b2-105">`RequiredArgument`i `OverloadGroup` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c46b2-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
-   <span data-ttu-id="c46b2-106">Konieczne weryfikacji opartych na kodzie.</span><span class="sxs-lookup"><span data-stu-id="c46b2-106">Imperative code-based validation.</span></span>  
  
-   <span data-ttu-id="c46b2-107">Deklaracyjne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="c46b2-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="c46b2-108">`RequiredArgument`i `OverloadGroup` atrybuty wskazać, że niektóre argumenty w działaniu są wymagane.</span><span class="sxs-lookup"><span data-stu-id="c46b2-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="c46b2-109">Konieczne weryfikacji opartych na kodzie zapewnia prosty sposób działania w celu udostępnienia weryfikacji o sobie, a ograniczenia deklaratywne włączyć weryfikację o aktywności i ich relacji z zawierającego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c46b2-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="c46b2-110">Jeśli działanie nie jest prawidłowo skonfigurowany zgodnie z wymaganiami weryfikacji, zwracane są błędy sprawdzania poprawności i ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="c46b2-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="c46b2-111">Jeśli zawierającego przepływu pracy został utworzony za pomocą projektanta przepływów pracy, wszelkie błędy sprawdzania poprawności i ostrzeżenia są wyświetlane w projektancie.</span><span class="sxs-lookup"><span data-stu-id="c46b2-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="c46b2-112">Jeśli przepływ pracy został utworzony poza projektanta przepływów pracy jakieś błędy sprawdzania poprawności są zwracane, gdy jest wywoływana przez przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="c46b2-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="c46b2-113">Niezależnie od sposobu utworzenia przepływu pracy przepływ pracy z błędami sprawdzania poprawności nigdy nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="c46b2-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="c46b2-114">Ta sekcja zawiera omówienie tych typów sprawdzania poprawności działania i sposób wywoływania sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="c46b2-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c46b2-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c46b2-115">In This Section</span></span>  
 [<span data-ttu-id="c46b2-116">Wymagane argumenty i grupy metod przeciążonych</span><span class="sxs-lookup"><span data-stu-id="c46b2-116">Required Arguments and Overload Groups</span></span>](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 <span data-ttu-id="c46b2-117">Informacje dotyczące używania `RequiredArgument` i `OverloadGroup` atrybutów w celu udostępnienia weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="c46b2-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="c46b2-118">Weryfikacja opartej na kodzie imperatywne</span><span class="sxs-lookup"><span data-stu-id="c46b2-118">Imperative Code-Based Validation</span></span>](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 <span data-ttu-id="c46b2-119">Informacje dotyczące używania weryfikacji opartych na kodzie dla <xref:System.Activities.CodeActivity> i <xref:System.Activities.NativeActivity> na podstawie działań.</span><span class="sxs-lookup"><span data-stu-id="c46b2-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="c46b2-120">Ograniczenia deklaratywne</span><span class="sxs-lookup"><span data-stu-id="c46b2-120">Declarative Constraints</span></span>](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 <span data-ttu-id="c46b2-121">Informacje dotyczące używania deklaratywne ograniczenia do udostępnienia weryfikacji działania złożonego.</span><span class="sxs-lookup"><span data-stu-id="c46b2-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="c46b2-122">Wywoływanie sprawdzania poprawności działania</span><span class="sxs-lookup"><span data-stu-id="c46b2-122">Invoking Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 <span data-ttu-id="c46b2-123">W tym artykule omówiono podczas sprawdzania poprawności działania jest wywoływana automatycznie oraz sposób jawnego wywołania sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="c46b2-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c46b2-124">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c46b2-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c46b2-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c46b2-125">Related Sections</span></span>
