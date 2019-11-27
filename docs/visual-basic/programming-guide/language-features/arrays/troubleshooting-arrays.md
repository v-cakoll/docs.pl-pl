---
title: Rozwiązywanie problemów związanych z tablicami
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 3c50c68c2a39aa04cff2dd43b5dfde709aec290f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349066"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Rozwiązywanie problemów związanych z tablicami (Visual Basic)
Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy z tablicami.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Błędy kompilacji deklarujące i inicjujące tablicę  
 Błędy kompilacji mogą wynikać z nieporozumienia reguł do deklarowania, tworzenia i inicjowania tablic. Najczęstszymi przyczynami błędów są następujące:  
  
- Dostarczenie [nowej klauzuli operatora](../../../../visual-basic/language-reference/operators/new-operator.md) po określeniu długości wymiarów w deklaracji zmiennej tablicowej. Poniższe wiersze kodu pokazują nieprawidłowe deklaracje tego typu.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- Określanie długości wymiarów dla więcej niż tablicy najwyższego poziomu tablicy nieregularnej. Poniższy wiersz kodu przedstawia nieprawidłową deklarację tego typu.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- Pomijanie słowa kluczowego `New` podczas określania wartości elementów. Poniższy wiersz kodu przedstawia nieprawidłową deklarację tego typu.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- Dostarczanie klauzuli `New` bez nawiasów klamrowych (`{}`). Poniższe wiersze kodu pokazują nieprawidłowe deklaracje tego typu.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Uzyskiwanie dostępu do tablicy poza granicami  
 Proces inicjowania tablicy przypisuje górną granicę i dolną granicę dla każdego wymiaru. Każdy dostęp do elementu tablicy musi określać prawidłowy indeks (lub dolny) dla każdego wymiaru. Jeśli indeks jest niższy od jego dolnej granicy lub przekracza górną granicę, <xref:System.IndexOutOfRangeException> powoduje wyjątek. Kompilator nie może wykryć takiego błędu, dlatego wystąpi błąd w czasie wykonywania.  
  
### <a name="determining-bounds"></a>Określanie granic  
 Jeśli inny składnik przekazuje tablicę do kodu, na przykład jako argument procedury, nie jest znany rozmiar tej tablicy lub długość jej wymiarów. Należy zawsze określić górną granicę dla każdego wymiaru tablicy przed podjęciem próby dostępu do dowolnych elementów. Jeśli tablica została utworzona za pomocą pewnych metod innych niż klauzula `New` Visual Basic, Dolna granica może być coś innego niż 0 i jest najbezpieczniejsza, aby określić, że jest to Dolna granica.  
  
### <a name="specifying-the-dimension"></a>Określanie wymiaru  
 Podczas określania granic tablicy wielowymiarowej należy zadbać o to, aby określić wymiar. `dimension` parametry metody <xref:System.Array.GetLowerBound%2A> i <xref:System.Array.GetUpperBound%2A> są oparte na 0, a `Rank` parametry Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> i <xref:Microsoft.VisualBasic.Information.UBound%2A> są oparte na 1.  
  
## <a name="see-also"></a>Zobacz także

- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Instrukcje: Inicjowanie zmiennej tablicowej w Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
