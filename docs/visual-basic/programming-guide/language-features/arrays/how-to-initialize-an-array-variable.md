---
title: 'Instrukcje: inicjowanie zmiennej tablicy'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 7feaf71fa1c59c24aa751f2b9e28328d47ba357c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413069"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Porady: inicjowanie zmiennej tablicy w języku Visual Basic
Można zainicjować zmienną tablicową przez uwzględnienie literału tablicy w `New` klauzuli i określenie wartości początkowych tablicy. Można określić typ lub zezwolić na wywnioskowanie go na podstawie wartości w literale tablicy. Aby uzyskać więcej informacji na temat sposobu wywnioskowania typu, zobacz "zapełnianie tablicy wartościami początkowymi" w [tablicach](index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Aby zainicjować zmienną tablicową przy użyciu literału tablicowego  
  
- W `New` klauzuli lub po przypisaniu wartości tablicy podaj wartości elementów w nawiasach klamrowych ( `{}` ). W poniższym przykładzie przedstawiono kilka sposobów deklarowania, tworzenia i inicjowania zmiennej, która zawiera tablicę z elementami typu `Char` .  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Po wykonaniu każdej instrukcji Utworzona tablica ma długość 3, z elementami w indeksie od 0 do indeksu 2 zawierającego wartości początkowe. Jeśli podasz górną granicę i wartości, musisz dołączyć wartość dla każdego elementu z indeksu od 0 do górnej granicy.  
  
     Należy zauważyć, że nie ma potrzeby określania górnej granicy indeksu, jeśli podasz wartości elementów w literale tablicowym. Jeśli nie określono górnej granicy, rozmiar tablicy jest wywnioskowany na podstawie liczby wartości w literale tablicy.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Aby zainicjować wielowymiarową zmienną tablicową przy użyciu literałów tablicy  
  
- Zagnieżdżaj wartości w nawiasach klamrowych ( `{}` ) w nawiasach klamrowych. Upewnij się, że zagnieżdżona tablica literałów wszystkie wnioskowanie jako tablice tego samego typu i długości. Poniższy przykład kodu pokazuje kilka przykładów inicjalizacji tablicy wielowymiarowej.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- Można jawnie określić granice tablicy lub pozostawić je, a kompilator wywnioskuje granice tablicy na podstawie wartości w literale tablicy. Jeśli podasz górną granicę i wartości, musisz dołączyć wartość dla każdego elementu z indeksu od 0 do górnej granicy w każdym wymiarze. W poniższym przykładzie przedstawiono kilka sposobów deklarowania, tworzenia i inicjowania zmiennej, która zawiera dwuwymiarową tablicę, która zawiera elementy typu`Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Po wykonaniu każdej instrukcji Utworzona tablica zawiera sześć zainicjowanych elementów, które mają indeksy `(0,0)` , `(0,1)` , `(0,2)` ,, `(1,0)` `(1,1)` i `(1,2)` . Każda lokalizacja tablicy zawiera wartość `10` .  
  
- Poniższy przykład wykonuje iterację przez tablicę wielowymiarową. W aplikacji konsolowej systemu Windows, która jest zapisywana w Visual Basic, wklej kod wewnątrz `Sub Main()` metody. Ostatnie komentarze zawierają dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Aby zainicjować nieregularną zmienną tablicową przy użyciu literałów tablicy  
  
- Zagnieżdżaj wartości obiektów wewnątrz nawiasów klamrowych ( `{}` ). Chociaż można zagnieżdżać literały tablicowe, które określają tablice o różnych długościach, w przypadku tablicy nieregularnej, należy się upewnić, że zagnieżdżone literały tablicowe są ujęte w nawiasy ( `()` ). Nawiasy wymuszają Obliczanie zagnieżdżonych literałów tablicowych, a wyniki tablic są używane jako początkowe wartości tablicy nieregularnej. Poniższy przykład kodu przedstawia dwa przykłady inicjalizacji tablicy nieregularnej.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- Poniższy przykład wykonuje iterację przez tablicę nieregularną. W aplikacji konsolowej systemu Windows, która jest zapisywana w Visual Basic, wklej kod wewnątrz `Sub Main()` metody.  Ostatnie komentarze w kodzie przedstawiają dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Zobacz też

- [Tablice](index.md)
- [Rozwiązywanie problemów związanych z tablicami](troubleshooting-arrays.md)
