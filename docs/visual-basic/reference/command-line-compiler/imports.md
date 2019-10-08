---
title: -Imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005562"
---
# <a name="-imports-visual-basic"></a>-Imports (Visual Basic)
Importuje przestrzenie nazw z określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespaceList`|Wymagany. Rozdzielana przecinkami lista przestrzeni nazw do zaimportowania.|  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-imports` importuje wszystkie przestrzenie nazw zdefiniowane w bieżącym zestawie plików źródłowych lub z dowolnego przywoływanego zestawu.  
  
 Elementy członkowskie w przestrzeni nazw określonej przy użyciu `-imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji. Użyj [instrukcji Imports (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) , aby użyć przestrzeni nazw w jednym pliku kodu źródłowego.  
  
|Aby ustawić/Imports — w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **odwołania** .<br />3. Wprowadź nazwę przestrzeni nazw w polu obok przycisku **Dodaj użytkownika importowania** .<br />4. kliknij przycisk **Dodaj Import użytkownika** .|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje, gdy zostanie określony `/imports:system.globalization`. Niepowodzenie kompilacji wymaga, aby instrukcja `Imports System.Globalization` była uwzględniona na początku pliku kodu źródłowego lub że właściwość jest w pełni kwalifikowana jako `System.Globalization.CultureInfo.CurrentCulture.Name`.

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
