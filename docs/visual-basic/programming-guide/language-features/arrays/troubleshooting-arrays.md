---
title: Rozwiązywanie problemów związanych z tablicami (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833376"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Rozwiązywanie problemów związanych z tablicami (Visual Basic)
Ta strona zawiera listę niektórych typowych problemów, które mogą wystąpić podczas pracy z tablicami.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Błędy kompilacji deklarowania i inicjowania tablicy  
 Błędy kompilacji mogą wynikać z nieporozumienia reguły deklarowania, tworzenia i inicjowania tablic. Najbardziej typowe przyczyny błędów są następujące:  
  
-   Dostarczanie [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzuli po określeniu długości wymiarów w deklaracji zmiennej tablicy. Następujące wiersze kodu pokazują nieprawidłowe deklarację tego typu.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Określenie długości wymiarów dla więcej niż najwyższego poziomu tablicy nieregularnej tablicy. Następujący wiersz kodu zawiera nieprawidłowy deklaracja tego typu.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Pominięcie `New` — słowo kluczowe podczas określania wartości elementu. Następujący wiersz kodu zawiera nieprawidłowy deklaracja tego typu.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Dostarczanie `New` klauzuli bez nawiasów klamrowych (`{}`). Następujące wiersze kodu pokazują nieprawidłowe deklarację tego typu.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Uzyskiwanie dostępu do tablicy poza zakresem  
 Proces inicjowania tablicy przypisuje górną granicę i dolną granicę każdego wymiaru. Każdy dostęp do elementu tablicy, należy określić prawidłowy indeksu lub indeksu dolnego, dla każdego wymiaru. W przypadku dowolnego indeksu poniżej dolna lub powyżej jego górnej granicy <xref:System.IndexOutOfRangeException> wynikiem będzie wyjątek. Kompilator nie może wykryć takiego komunikatu o błędzie, więc wystąpi błąd w czasie wykonywania.  
  
### <a name="determining-bounds"></a>Określanie granice  
 Jeśli inny składnik przekazuje tablicę do kodu, na przykład jako argumentu procedury nie znasz rozmiaru tablicy lub długości jej wymiarów. Przed przystąpieniem do dostępu do żadnych elementów, należy zawsze określić górną granicę dla każdego wymiaru tablicy. Jeśli tablica została utworzona przy użyciu niektórych metod innych niż w języku Visual Basic `New` klauzuli dolna granica może być coś innego niż 0 i jest najbezpieczniejszy określić również tego dolna granica.  
  
### <a name="specifying-the-dimension"></a>Określanie wymiaru  
 Podczas określania granice tablicy wielowymiarowej, powinien zachować ostrożność, jak określić wymiaru. `dimension` Parametry <xref:System.Array.GetLowerBound%2A> i <xref:System.Array.GetUpperBound%2A> metody są oparte na 0, podczas `Rank` parametry języka Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> i <xref:Microsoft.VisualBasic.Information.UBound%2A> funkcje są oparte na 1.  
  
## <a name="see-also"></a>Zobacz także

- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
