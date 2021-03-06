---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: cc9fc222843bdfe8e49d2d291dc36ff3e0c63fc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408598"
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
 `-imports`Opcja importuje wszystkie przestrzenie nazw zdefiniowane w bieżącym zestawie plików źródłowych lub z dowolnego zestawu, do którego się odwołuje.  
  
 Elementy członkowskie w przestrzeni nazw określonej za pomocą `-imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji. Użyj [instrukcji Imports (przestrzeń nazw i typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) , aby użyć przestrzeni nazw w jednym pliku kodu źródłowego.  
  
|Aby ustawić Importy w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **odwołania** .<br />3. Wprowadź nazwę przestrzeni nazw w polu obok przycisku **Dodaj użytkownika importowania** .<br />4. kliknij przycisk **Dodaj Import użytkownika** .|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje, kiedy `-imports:system.globalization` jest określony. Bez tej operacji kompilacja wymaga, aby `Imports System.Globalization` instrukcja była uwzględniona na początku pliku kodu źródłowego lub że właściwość jest w pełni kwalifikowana jako `System.Globalization.CultureInfo.CurrentCulture.Name` .

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Referencje i instrukcja Imports](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
