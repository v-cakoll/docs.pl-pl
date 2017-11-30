---
title: "Zła długość rekordu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
