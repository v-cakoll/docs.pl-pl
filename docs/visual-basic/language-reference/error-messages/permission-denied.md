---
title: Odmowa uprawnień (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: ad75c556748bf5c0f9cef55310c4ffa7b01fd458
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920838"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="e77a5-102">Odmowa uprawnień (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e77a5-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="e77a5-103">Nastąpiła próba zapisu na dysk chroniony przed zapisem lub uzyskania dostępu do pliku zablokowane.</span><span class="sxs-lookup"><span data-stu-id="e77a5-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e77a5-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e77a5-104">To correct this error</span></span>  
  
1. <span data-ttu-id="e77a5-105">Aby otworzyć plik chroniony przed zapisem, zmień atrybut zabezpieczenie przed zapisem z pliku.</span><span class="sxs-lookup"><span data-stu-id="e77a5-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2. <span data-ttu-id="e77a5-106">Upewnij się, że inny proces nie zablokował plik, a następnie poczekaj, aby otworzyć plik, aż inny proces, zwalnia go.</span><span class="sxs-lookup"><span data-stu-id="e77a5-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3. <span data-ttu-id="e77a5-107">Dostęp do rejestru, sprawdź, czy uprawnienia użytkownika i obejmują ten typ dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="e77a5-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77a5-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e77a5-108">See also</span></span>

- [<span data-ttu-id="e77a5-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="e77a5-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
