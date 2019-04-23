---
title: Zła długość rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 1bc75303bcc2f46e54c06e89347da28997e59786
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979746"
---
# <a name="bad-record-length"></a><span data-ttu-id="9c5f2-102">Zła długość rekordu</span><span class="sxs-lookup"><span data-stu-id="9c5f2-102">Bad record length</span></span>
<span data-ttu-id="9c5f2-103">Wśród możliwe przyczyny tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="9c5f2-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="9c5f2-104">Długość określone w zmiennej rekordu `FileGet`, `FileGetObject`, `FilePut` lub `FilePutObject` instrukcji różni się od długości określonej w odpowiednich `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9c5f2-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="9c5f2-105">Zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg znaków o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="9c5f2-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="9c5f2-106">Zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` typu.</span><span class="sxs-lookup"><span data-stu-id="9c5f2-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c5f2-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9c5f2-107">To correct this error</span></span>  
  
1. <span data-ttu-id="9c5f2-108">Upewnij się, sumę rozmiarów zmiennych o stałej długości w typ zdefiniowany przez użytkownika, definiująca typ zmiennej rekordu jest taki sam, jak wartość podana w `FileOpen` instrukcji `Len` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9c5f2-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="9c5f2-109">Jeśli zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg znaków o zmiennej długości, upewnij się, ciąg znaków o zmiennej długości jest mniejsza niż długość rekordu określana w co najmniej 2 znaki `Len` klauzuli `FileOpen` Instrukcja.</span><span class="sxs-lookup"><span data-stu-id="9c5f2-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="9c5f2-110">Jeśli zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` upewnij się, ciąg znaków o zmiennej długości jest mniejsza niż długość rekordu określana w co najmniej 4 bajtów `Len` klauzuli `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9c5f2-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c5f2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c5f2-111">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
