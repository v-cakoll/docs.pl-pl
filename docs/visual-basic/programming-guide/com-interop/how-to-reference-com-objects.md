---
title: 'Porady: odwołania do obiektów COM z Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 49f3da396ca5cd48b0cf454ce1ecd5422c28e38f
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199368"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Porady: odwołania do obiektów COM z Visual Basic
W języku Visual Basic dodanie odwołania do obiektów COM, które mają bibliotek typów wymaga utworzenia zestawu międzyoperacyjnego dla biblioteki COM. Odwołania do elementów członkowskich obiektu COM są kierowane do zestawu międzyoperacyjnego, a następnie przekazywane do rzeczywistego obiektu COM. Odpowiedzi z obiektu COM są kierowane do zestawu międzyoperacyjnego i przekazywane do usługi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji.  
  
 Obiekt COM można odwoływać się bez użycia zestaw międzyoperacyjny przez osadzanie informacji o typie dla obiektu COM w zestawie .NET. Aby osadzić informacje o typie, należy ustawić `Embed Interop Types` właściwość `True` odwołania do obiektu COM. Jeśli kompilujesz za pomocą kompilatora wiersza polecenia, użyj `/link` opcję, aby odwoływać się do biblioteki COM. Aby uzyskać więcej informacji, zobacz [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Po dodaniu odwołania do biblioteki typów z zintegrowanego środowiska programistycznego (IDE) Visual Basic automatycznie tworzy zestawy międzyoperacyjne. Podczas pracy z poziomu wiersza polecenia, można użyć narzędzia Tlbimp, aby ręcznie utworzyć zestawy międzyoperacyjne.  
  
### <a name="to-add-references-to-com-objects"></a>Aby dodać odwołania do obiektów COM  
  
1.  Na **projektu** menu, wybierz **Dodaj odwołanie** a następnie kliknij przycisk **COM** karty w oknie dialogowym.  
  
2.  Wybierz składnik, który chcesz używać, z listy obiektów COM.  
  
3.  Aby uprościć dostęp do zestawu międzyoperacyjnego, należy dodać `Imports` instrukcji na górze klasę lub moduł, w której będzie używać obiektu COM. Na przykład, poniższy kod importuje przestrzeń nazw `INKEDLib` dla obiektów, do którego odwołuje się `Microsoft InkEdit Control 1.0` biblioteki.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Aby utworzyć zestaw międzyoperacyjny przy użyciu Tlbimp  
  
1.  Dodaj lokalizację testowanego Tlbimp do ścieżki wyszukiwania, jeśli nie jest już częścią ścieżki wyszukiwania, a nie jesteś obecnie w katalogu, w którym znajduje się.  
  
2.  Wywołanie Tlbimp z wiersza polecenia, podając następujące informacje:  
  
    -   Nazwa i lokalizacja pliku dll, który zawiera biblioteki typów  
  
    -   Nazwa i lokalizacja przestrzeni nazw, gdzie ma zostać umieszczony informacje  
  
    -   Nazwy i lokalizacji docelowych zestawu międzyoperacyjnego  
  
     Poniższy kod stanowi przykład:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp umożliwia tworzenie usług międzyoperacyjnych dla biblioteki typów, nawet w przypadku niezarejestrowanych obiektów COM. Jednak z obiektami COM, które odwołują się zestawy międzyoperacyjne musi być poprawnie zarejestrowany na komputerze, na którym mają być użyte do. Obiekt COM można zarejestrować za pomocą narzędzia Regsvr32 dołączone do systemu operacyjnego Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (eksporter biblioteki typów)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Przewodnik: wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Rozwiązywanie problemów związanych z współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
