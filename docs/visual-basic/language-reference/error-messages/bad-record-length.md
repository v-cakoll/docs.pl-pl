---
title: Zła długość rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 1bc75303bcc2f46e54c06e89347da28997e59786
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979746"
---
# <a name="bad-record-length"></a>Zła długość rekordu
Wśród możliwe przyczyny tego błędu są:  
  
-   Długość określone w zmiennej rekordu `FileGet`, `FileGetObject`, `FilePut` lub `FilePutObject` instrukcji różni się od długości określonej w odpowiednich `FileOpen` instrukcji.  
  
-   Zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg znaków o zmiennej długości.  
  
-   Zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` typu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, sumę rozmiarów zmiennych o stałej długości w typ zdefiniowany przez użytkownika, definiująca typ zmiennej rekordu jest taki sam, jak wartość podana w `FileOpen` instrukcji `Len` klauzuli.  
  
2. Jeśli zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg znaków o zmiennej długości, upewnij się, ciąg znaków o zmiennej długości jest mniejsza niż długość rekordu określana w co najmniej 2 znaki `Len` klauzuli `FileOpen` Instrukcja.  
  
3. Jeśli zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` upewnij się, ciąg znaków o zmiennej długości jest mniejsza niż długość rekordu określana w co najmniej 4 bajtów `Len` klauzuli `FileOpen` instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
