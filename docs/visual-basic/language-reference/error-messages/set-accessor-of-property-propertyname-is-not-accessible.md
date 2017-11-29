---
title: "&#39; Ustaw &#39; Akcesor właściwości &#39; &lt;propertyname&gt;&#39; nie jest dostępny"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords: BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39; Ustaw &#39; Akcesor właściwości &#39; &lt;propertyname&gt;&#39; nie jest dostępny
Instrukcja próbuje zapisać wartości właściwości, gdy nie ma dostępu do właściwości `Set` procedury.  
  
 Jeśli [Instrukcja Set](../../../visual-basic/language-reference/statements/set-statement.md) jest oznaczony atrybutem bardziej restrykcyjnego dostępu niż poziom jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), podjęto próbę ustawienia wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:  
  
-   `Set` Instrukcji jest oznaczony jako [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.  
  
-   `Set` Instrukcji jest oznaczony jako [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie w klasy lub struktury, w którym jest zdefiniowana właściwość ani w klasie pochodnej.  
  
-   `Set` Instrukcji jest oznaczony jako [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.  
  
 **Identyfikator błędu:** BC31102  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli masz kontroli kodu źródłowego Definiowanie właściwości, zaleca się zadeklarowanie `Set` procedurę za pomocą tego samego poziomu dostępu, co samej właściwości.  
  
-   Jeśli nie masz kontroli kodu źródłowego Definiowanie właściwości lub należy ograniczyć `Set` procedury więcej niż właściwość, spróbuj przenieść instrukcji, która ustawia wartości właściwości w regionie kod, który ma lepszy dostęp do poziomu dostępu Właściwość.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury własności](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
