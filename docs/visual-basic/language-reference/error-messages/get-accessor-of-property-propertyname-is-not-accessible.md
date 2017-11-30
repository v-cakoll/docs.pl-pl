---
title: "&#39; Pobierz &#39; Akcesor właściwości &#39; &lt;propertyname&gt;&#39; nie jest dostępny"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords: BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39; Pobierz &#39; Akcesor właściwości &#39; &lt;propertyname&gt;&#39; nie jest dostępny
Instrukcję próbuje pobrać wartość właściwości, gdy nie ma dostępu do właściwości `Get` procedury.  
  
 Jeśli [instrukcja Get](../../../visual-basic/language-reference/statements/get-statement.md) jest oznaczony atrybutem bardziej restrykcyjnego dostępu niż poziom jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), próba odczytu wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:  
  
-   `Get` Instrukcji jest oznaczony jako [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.  
  
-   `Get` Instrukcji jest oznaczony jako [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie w klasy lub struktury, w którym jest zdefiniowana właściwość ani w klasie pochodnej.  
  
-   `Get` Instrukcji jest oznaczony jako [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.  
  
 **Identyfikator błędu:** BC31103  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli masz kontroli kodu źródłowego Definiowanie właściwości, zaleca się zadeklarowanie `Get` procedurę za pomocą tego samego poziomu dostępu, co samej właściwości.  
  
-   Jeśli nie masz kontroli kodu źródłowego Definiowanie właściwości lub należy ograniczyć `Get` procedury więcej niż właściwość, spróbuj przenieść instrukcji, która odczytuje wartość właściwości region kodu, który ma lepszy dostęp do poziomu dostępu Właściwość.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury własności](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
