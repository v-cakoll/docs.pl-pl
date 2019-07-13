---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858598"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="1bfff-101">Wartości null coalescer nie są widoczne w debugerze, dopóki jeden krok później</span><span class="sxs-lookup"><span data-stu-id="1bfff-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1bfff-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1bfff-102">Details</span></span>|<span data-ttu-id="1bfff-103">Usterki w programie .NET Framework 4.5 powoduje, że wartości ustawione za pośrednictwem o wartości null operacji łączącego nie powinny być widoczne w debugerze natychmiast po zakończeniu operacji przypisania jest wykonywany podczas uruchamiania na 64-bitowej wersji Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfff-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="1bfff-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1bfff-104">Suggestion</span></span>|<span data-ttu-id="1bfff-105">Przechodzenie krok po kroku jeden dodatkowy czas w debugerze spowoduje, że lokalne/pola. wartość do zaktualizowania poprawnie.</span><span class="sxs-lookup"><span data-stu-id="1bfff-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="1bfff-106">Ponadto ten problem został rozwiązany w .NET Framework 4.6; Uaktualnianie do wersji Framework powinno rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="1bfff-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="1bfff-107">Scope</span><span class="sxs-lookup"><span data-stu-id="1bfff-107">Scope</span></span>|<span data-ttu-id="1bfff-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="1bfff-108">Edge</span></span>|
|<span data-ttu-id="1bfff-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="1bfff-109">Version</span></span>|<span data-ttu-id="1bfff-110">4.5</span><span class="sxs-lookup"><span data-stu-id="1bfff-110">4.5</span></span>|
|<span data-ttu-id="1bfff-111">Typ</span><span class="sxs-lookup"><span data-stu-id="1bfff-111">Type</span></span>|<span data-ttu-id="1bfff-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1bfff-112">Runtime</span></span>|

