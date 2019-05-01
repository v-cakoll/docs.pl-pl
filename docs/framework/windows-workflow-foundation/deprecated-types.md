---
title: Przestarzałe typy w programie Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: d41bf147cd079a3d6d3714da5595732de3dcb7de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774052"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="2410d-102">Przestarzałe typy w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="2410d-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="2410d-103">W .NET 4 zespołu przepływu pracy zwolnione wszystkich nowych aparatu przepływu pracy w <xref:System.Activities> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2410d-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="2410d-104">Wersja programu .NET 4.5 w wersji Beta firma Microsoft oznaczanie większość typów w "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, i <xref:System.Workflow.Runtime> przestrzeni nazw jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="2410d-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="2410d-105">Przestarzałe przestrzenie nazw i narzędzia</span><span class="sxs-lookup"><span data-stu-id="2410d-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="2410d-106">Następujące zestawy mają jeden lub więcej typów publicznych, które staną się przestarzałe:</span><span class="sxs-lookup"><span data-stu-id="2410d-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
- <span data-ttu-id="2410d-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="2410d-107">System.Workflow.Activities.dll</span></span>  
  
- <span data-ttu-id="2410d-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="2410d-108">System.Workflow.ComponentModel.dll</span></span>  
  
- <span data-ttu-id="2410d-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="2410d-109">System.Workflow.Runtime.dll</span></span>  
  
- <span data-ttu-id="2410d-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="2410d-110">System.WorkflowServices.dll</span></span>  
  
- <span data-ttu-id="2410d-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="2410d-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
- <span data-ttu-id="2410d-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="2410d-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
- <span data-ttu-id="2410d-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="2410d-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="2410d-114">W rezultacie klienci, którzy używają przestarzałych API 3 WF będą napotykać ostrzeżenia kompilacji za pomocą komunikatu podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="2410d-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="2410d-115">**Ostrzeżenie BC40000: X jest przestarzała: WF 3 typy są przestarzałe. Zamiast tego użyj WF 4.**</span><span class="sxs-lookup"><span data-stu-id="2410d-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="2410d-116">Typy zostanie usunięty z programu .NET Framework w przyszłej wersji, ale nie Ustaliliśmy jeszcze tego przedziału czasu (nie w 4.5).</span><span class="sxs-lookup"><span data-stu-id="2410d-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="2410d-117">Ten krok bieżącego pozwala nam komunikować się z naszym kierunek dla naszych klientów i zezwolić im na może zająć dużo czasu, aby przejść do nowego modelu WF4.</span><span class="sxs-lookup"><span data-stu-id="2410d-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="2410d-118">Firma Microsoft oczywiście, będzie obsługiwać te typy WF 3 w obszarze [zasady świadczenia pomocy technicznej firmy Microsoft](https://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="2410d-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](https://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="2410d-119">Istniejące aplikacje WF3 uruchomią się bez problemu w .NET 4.5 i programu Visual Studio 2012 będzie obsługiwać nowych i istniejących rozwiązań opartych na WF3.</span><span class="sxs-lookup"><span data-stu-id="2410d-119">Existing WF3 applications will run without issue on .NET 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="2410d-120">Zasady dotyczące typów w <xref:System.Workflow.Activities.Rules> przestrzeni nazw, które nie mają zastępuje w programie WF 4.5, nie są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="2410d-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="2410d-121">Klienci, którzy chcą przeprowadzić migrację aplikacji WF 4 znajdą się w Pomocy [wskazówek dotyczących migracji 4 przepływu pracy](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="2410d-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
