---
title: Zestaw nie jest obsługiwane w czasie wykonywania
ms.date: 07/20/2015
f1_keywords:
- vbrID382
ms.assetid: cb7285d3-778f-423d-a2be-88573be8ad48
ms.openlocfilehash: 1b3f8aa3811baae240e6baa546082d0dcf2cf667
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325868"
---
# <a name="set-not-supported-at-run-time"></a><span data-ttu-id="f0263-102">Zestaw nie jest obsługiwane w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="f0263-102">Set not supported at run time</span></span>
<span data-ttu-id="f0263-103">Próbowano ustawić lub zmienić właściwości, których wartość można ustawić tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f0263-103">You tried to set or change a property whose value can only be set at design time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f0263-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f0263-104">To correct this error</span></span>  
  
1. <span data-ttu-id="f0263-105">Usuń odwołanie do właściwości w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f0263-105">Remove the reference to the property from your code.</span></span>  
  
2. <span data-ttu-id="f0263-106">Zmień odwołania, aby zwracać tylko wartości właściwości w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f0263-106">Change the reference to only return the value of the property at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0263-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0263-107">See also</span></span>

- [<span data-ttu-id="f0263-108">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f0263-108">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
