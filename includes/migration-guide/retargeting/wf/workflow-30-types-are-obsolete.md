---
ms.openlocfilehash: 70acbb571921c5f72ecaa26b26136a77532ad220
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774457"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="a33d4-101">Typy przepływów pracy w wersji 3.0 są przestarzałe</span><span class="sxs-lookup"><span data-stu-id="a33d4-101">WorkFlow 3.0 types are obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a33d4-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a33d4-102">Details</span></span>|<span data-ttu-id="a33d4-103">Interfejsy API programu Windows Workflow Foundation (WWF) 3.0 (te z przestrzeni nazw System.Workflow) są obecnie przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="a33d4-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>|
|<span data-ttu-id="a33d4-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a33d4-104">Suggestion</span></span>|<span data-ttu-id="a33d4-105">Zamiast nich należy używać nowych interfejsów API programu WWF 4.0 (w System.Activities).</span><span class="sxs-lookup"><span data-stu-id="a33d4-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="a33d4-106">Przykład korzystania z nowych interfejsów API można znaleźć [tutaj](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), a dalsze wskazówki są dostępne [tutaj](https://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx).</span><span class="sxs-lookup"><span data-stu-id="a33d4-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](https://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx).</span></span> <span data-ttu-id="a33d4-107">Ponieważ interfejsy API WWF 3.0 są nadal obsługiwane, alternatywnym rozwiązaniem może być używanie ich i pominięcie ostrzeżenia podczas kompilacji lub użycie starszego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a33d4-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>|
|<span data-ttu-id="a33d4-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="a33d4-108">Scope</span></span>|<span data-ttu-id="a33d4-109">Duży</span><span class="sxs-lookup"><span data-stu-id="a33d4-109">Major</span></span>|
|<span data-ttu-id="a33d4-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="a33d4-110">Version</span></span>|<span data-ttu-id="a33d4-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a33d4-111">4.5</span></span>|
|<span data-ttu-id="a33d4-112">Typ</span><span class="sxs-lookup"><span data-stu-id="a33d4-112">Type</span></span>|<span data-ttu-id="a33d4-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="a33d4-113">Retargeting</span></span>|
