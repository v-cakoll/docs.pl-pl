---
title: Element „<name1>” jest niejednoznaczny, po imporcie z przestrzeni nazw lub typów „<name2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30561
- bc30561
helpviewer_keywords:
- BC30561
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
ms.openlocfilehash: 63e61d412e4d1238b08ccae94f11adb0c3d1b54d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401579"
---
# <a name="name1-is-ambiguous-imported-from-the-namespaces-or-types-name2"></a><span data-ttu-id="fa3eb-102">Element „\<name1>” jest niejednoznaczny, po imporcie z przestrzeni nazw lub typów „\<name2>”</span><span class="sxs-lookup"><span data-stu-id="fa3eb-102">'\<name1>' is ambiguous, imported from the namespaces or types '\<name2>'</span></span>
<span data-ttu-id="fa3eb-103">Podana nazwa jest niejednoznaczna i dlatego powoduje konflikt z inną nazwą.</span><span class="sxs-lookup"><span data-stu-id="fa3eb-103">You have provided a name that is ambiguous and therefore conflicts with another name.</span></span> <span data-ttu-id="fa3eb-104">Kompilator Visual Basic nie ma żadnych reguł rozwiązywania konfliktów; należy samodzielnie odróżnić nazwy.</span><span class="sxs-lookup"><span data-stu-id="fa3eb-104">The Visual Basic compiler does not have any conflict resolution rules; you must disambiguate names yourself.</span></span>  
  
 <span data-ttu-id="fa3eb-105">**Identyfikator błędu:** BC30561</span><span class="sxs-lookup"><span data-stu-id="fa3eb-105">**Error ID:** BC30561</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa3eb-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fa3eb-106">To correct this error</span></span>  
  
1. <span data-ttu-id="fa3eb-107">Usuń niejednoznaczność nazwy, usuwając Importy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fa3eb-107">Disambiguate the name by removing namespace imports.</span></span>  
  
2. <span data-ttu-id="fa3eb-108">W pełni Zakwalifikuj nazwę.</span><span class="sxs-lookup"><span data-stu-id="fa3eb-108">Fully qualify the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3eb-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa3eb-109">See also</span></span>

- [<span data-ttu-id="fa3eb-110">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="fa3eb-110">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="fa3eb-111">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa3eb-111">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="fa3eb-112">Namespace — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="fa3eb-112">Namespace Statement</span></span>](../statements/namespace-statement.md)
