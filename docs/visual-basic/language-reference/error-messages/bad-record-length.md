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
---
# <a name="bad-record-length"></a>Zła długość rekordu
Wśród możliwych przyczyn tego błędu są:  
  
-   Długość określona w zmiennej rekordu `FileGet`, `FileGetObject`, `FilePut` lub `FilePutObject` instrukcji różni się od długości określonej w polu `FileOpen` instrukcji.  
  
-   Zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg o zmiennej długości.  
  
-   Zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` typu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że suma rozmiarów zmiennych o stałej długości w typie użytkownika określenie typu zmienną rekordów jest taki sam, jak wartość podana w `FileOpen` w instrukcji `Len` klauzuli.  
  
2.  Jeśli zmienna w `FilePut` lub `FilePutObject` instrukcji jest lub zawiera ciąg o zmiennej długości, upewnij się, że ciąg o zmiennej długości jest krótszy niż długość rekordu określone w co najmniej 2 znaki `Len` klauzuli `FileOpen` instrukcji.  
  
3.  Jeśli zmienna w `FilePut` lub `FilePutObject` jest lub zawiera `Variant` upewnij się, że ciąg o zmiennej długości jest krótszy niż długość rekordu określony w co najmniej 4 bajtów `Len` klauzuli `FileOpen` instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
