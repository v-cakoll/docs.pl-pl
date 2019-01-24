---
title: Zła długość rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 37d9da67656ec4821903d8ba67a27ef10f1a437d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728870"
---
# <a name="bad-record-length"></a><span data-ttu-id="f4d8c-102">Zła długość rekordu</span><span class="sxs-lookup"><span data-stu-id="f4d8c-102">Bad record length</span></span>
<span data-ttu-id="f4d8c-103">Wśród możliwe przyczyny tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="f4d8c-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="f4d8c-104">Długość określone w zmiennej rekordu `FileGet`, `FileGetObject`, `FilePut` lub `FilePutObject` instrukcji różni się od długości określonej w odpowiednich `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f4d8c-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="f4d8c-105">Zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg znaków o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="f4d8c-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="f4d8c-106">Zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` typu.</span><span class="sxs-lookup"><span data-stu-id="f4d8c-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4d8c-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f4d8c-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="f4d8c-108">Upewnij się, sumę rozmiarów zmiennych o stałej długości w typ zdefiniowany przez użytkownika, definiująca typ zmiennej rekordu jest taki sam, jak wartość podana w `FileOpen` instrukcji `Len` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f4d8c-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="f4d8c-109">Jeśli zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg znaków o zmiennej długości, upewnij się, ciąg znaków o zmiennej długości jest mniejsza niż długość rekordu określana w co najmniej 2 znaki `Len` klauzuli `FileOpen` Instrukcja.</span><span class="sxs-lookup"><span data-stu-id="f4d8c-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="f4d8c-110">Jeśli zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` upewnij się, ciąg znaków o zmiennej długości jest mniejsza niż długość rekordu określana w co najmniej 4 bajtów `Len` klauzuli `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f4d8c-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d8c-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4d8c-111">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
