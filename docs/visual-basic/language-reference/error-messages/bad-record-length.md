---
title: Zła długość rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: b4b311e2eb504c485772091ed126b3beb71729cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585973"
---
# <a name="bad-record-length"></a><span data-ttu-id="d9796-102">Zła długość rekordu</span><span class="sxs-lookup"><span data-stu-id="d9796-102">Bad record length</span></span>
<span data-ttu-id="d9796-103">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="d9796-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="d9796-104">Długość określona w zmiennej rekordu `FileGet`, `FileGetObject`, `FilePut` lub `FilePutObject` instrukcji różni się od długości określonej w polu `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d9796-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="d9796-105">Zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="d9796-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="d9796-106">Zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` typu.</span><span class="sxs-lookup"><span data-stu-id="d9796-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9796-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d9796-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="d9796-108">Upewnij się, że suma rozmiarów zmiennych o stałej długości w typie użytkownika określenie typu zmienną rekordów jest taki sam, jak wartość podana w `FileOpen` w instrukcji `Len` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d9796-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="d9796-109">Jeśli zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg o zmiennej długości, upewnij się, że ciąg o zmiennej długości jest krótszy niż długość rekordu określone w co najmniej 2 znaki `Len` klauzuli `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d9796-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="d9796-110">Jeśli zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` upewnij się, że ciąg o zmiennej długości jest krótszy niż długość rekordu określony w co najmniej 4 bajtów `Len` klauzuli `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d9796-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9796-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9796-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
