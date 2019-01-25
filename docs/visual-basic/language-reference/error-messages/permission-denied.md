---
title: Odmowa uprawnień (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: 43ec20382a2043868fb54e2f472cb316ebfbd623
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717834"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="75e14-102">Odmowa uprawnień (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75e14-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="75e14-103">Nastąpiła próba zapisu na dysk chroniony przed zapisem lub uzyskania dostępu do pliku zablokowane.</span><span class="sxs-lookup"><span data-stu-id="75e14-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="75e14-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="75e14-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="75e14-105">Aby otworzyć plik chroniony przed zapisem, zmień atrybut zabezpieczenie przed zapisem z pliku.</span><span class="sxs-lookup"><span data-stu-id="75e14-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="75e14-106">Upewnij się, że inny proces nie zablokował plik, a następnie poczekaj, aby otworzyć plik, aż inny proces, zwalnia go.</span><span class="sxs-lookup"><span data-stu-id="75e14-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="75e14-107">Dostęp do rejestru, sprawdź, czy uprawnienia użytkownika i obejmują ten typ dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="75e14-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e14-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75e14-108">See also</span></span>
- [<span data-ttu-id="75e14-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="75e14-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
