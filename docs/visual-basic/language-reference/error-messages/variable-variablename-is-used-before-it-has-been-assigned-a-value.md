---
title: Zmienna „<variablename>” jest używana, zanim zostanie do niej przypisana wartość
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 23201b89f44f6384ae9f75d941d264e8d59bef80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268837"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>Zmienna "\<nazwa_zmiennej >" jest używana, zanim została do niej przypisana wartość
Zmienna "\<nazwa_zmiennej >" jest używana, zanim została do niej przypisana wartość. W czasie wykonywania może wystąpić wyjątek pustej referencji.  
  
 Aplikacja ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod, który odczytuje zmienną przed przypisaniem do niej dowolną wartość.  
  
 Jeśli zmienna nie zostanie przypisana wartość, zawiera wartość domyślna dla jego typu danych. Odwołanie do typu danych, że wartość domyślna to [nic](../../../visual-basic/language-reference/nothing.md). Odczytywanie zmienną odwołania, który ma wartość `Nothing` może spowodować, że <xref:System.NullReferenceException> w pewnych okolicznościach.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42104  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź logikę przepływu sterowania i upewnij się, że zmienna ma prawidłową wartość przed kontrola przechodzi do żadnej instrukcji, który odczyta go.  
  
-   Jest jednym ze sposobów, aby zagwarantować, że zmienna zawsze ma prawidłową wartość zainicjować go jako części swojej deklaracji. Zobacz sekcję "Inicjowanie" w [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Zobacz także
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Rozwiązywanie problemów związanych ze zmiennymi](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
