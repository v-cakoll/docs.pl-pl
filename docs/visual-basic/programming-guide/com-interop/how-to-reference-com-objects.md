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
ms.openlocfilehash: ea0e1d9b0ae9f151d901c425512508ba7bc05343
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524356"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Porady: odwołania do obiektów COM z Visual Basic
W Visual Basic Dodawanie odwołań do obiektów COM, które mają biblioteki typów, wymaga utworzenia zestawu międzyoperacyjnego dla biblioteki COM. Odwołania do elementów członkowskich obiektu COM są kierowane do zestawu międzyoperacyjnego, a następnie przekazywane do rzeczywistego obiektu COM. Odpowiedzi z obiektu COM są kierowane do zestawu międzyoperacyjnego i przekazywane do aplikacji .NET Framework.  
  
 Można odwołać się do obiektu COM bez użycia zestawu międzyoperacyjnego przez osadzenie informacji o typie dla obiektu COM w zestawie .NET. Aby osadzić informacje o typie, ustaw właściwość `Embed Interop Types` na `True` dla odwołania do obiektu COM. Jeśli kompilujesz przy użyciu kompilatora wiersza polecenia, użyj opcji `/link`, aby odwołać się do biblioteki COM. Aby uzyskać więcej informacji, zobacz [-link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Visual Basic automatycznie tworzy zestawy międzyoperacyjności podczas dodawania odwołania do biblioteki typów z zintegrowanego środowiska programistycznego (IDE). Podczas pracy z wiersza polecenia można użyć narzędzia Tlbimp do ręcznego tworzenia zestawów międzyoperacyjnych.  
  
### <a name="to-add-references-to-com-objects"></a>Aby dodać odwołania do obiektów COM  
  
1. W menu **projekt** wybierz polecenie **Dodaj odwołanie** , a następnie kliknij kartę **com** w oknie dialogowym.  
  
2. Wybierz składnik, którego chcesz użyć z listy obiektów COM.  
  
3. Aby uprościć dostęp do zestawu międzyoperacyjnego, Dodaj instrukcję `Imports` na początku klasy lub modułu, w którym będzie używany obiekt COM. Na przykład poniższy przykład kodu importuje przestrzeń nazw `INKEDLib` dla obiektów, do których odwołuje się biblioteka `Microsoft InkEdit Control 1.0`.  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Aby utworzyć zestaw międzyoperacyjny przy użyciu Tlbimp  
  
1. Dodaj lokalizację Tlbimp do ścieżki wyszukiwania, jeśli nie jest ona jeszcze częścią ścieżki wyszukiwania i nie znajduje się obecnie w katalogu, w którym się znajduje.  
  
2. Wywołaj Tlbimp z wiersza polecenia, dostarczając następujące informacje:  
  
    - Nazwa i lokalizacja biblioteki DLL zawierającej bibliotekę typów  
  
    - Nazwa i lokalizacja przestrzeni nazw, w której należy umieścić informacje  
  
    - Nazwa i lokalizacja docelowego zestawu międzyoperacyjnego  
  
     Poniższy kod zawiera przykład:  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Można użyć Tlbimp do tworzenia zestawów międzyoperacyjnych dla bibliotek typów, nawet dla niezarejestrowanych obiektów COM. Jednak obiekty COM, do których odwołują się zestawy międzyoperacyjności, muszą być poprawnie zarejestrowane na komputerze, na którym mają być używane. Obiekt COM można zarejestrować za pomocą narzędzia regsvr32 dołączonego do systemu operacyjnego Windows.  
  
## <a name="see-also"></a>Zobacz także

- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (importer biblioteki typów)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Przewodnik: wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Rozwiązywanie problemów związanych z współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
