---
title: "Porady: odwołania do obiektów COM z Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 694bd74e2b5ae374269accd845fe9178958bf56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Porady: odwołania do obiektów COM z Visual Basic
W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], dodawanie odwołań do obiektów COM, które mają bibliotek typów wymaga utworzenia zestaw międzyoperacyjny dla biblioteki COM. Odwołania do elementów członkowskich obiektu COM są kierowane do zestawu międzyoperacyjnego, a następnie przekazywane do rzeczywistego obiektu COM. Odpowiedzi z obiektu COM są kierowane do zestawu międzyoperacyjnego i przekazywane do Twojej [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikacji.  
  
 Obiekt COM można odwoływać się bez użycia zestawu międzyoperacyjnego osadzanie informacji o typie dla obiekt COM w ramach zestawu .NET. Osadzanie informacji o typie, ustaw `Embed Interop Types` właściwości `True` dla odwołania do obiektu COM. Jeśli kompilacja przy użyciu kompilatora wiersza polecenia, użyj `/link` opcję, aby odwołać biblioteki COM. Aby uzyskać więcej informacji, zobacz [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]automatycznie tworzy zestawy międzyoperacyjne podczas dodawania odwołania do biblioteki typów z zintegrowane środowisko programistyczne (IDE). Podczas pracy z poziomu wiersza polecenia, można użyć narzędzia Tlbimp ręcznie utworzyć zestawy międzyoperacyjne.  
  
### <a name="to-add-references-to-com-objects"></a>Aby dodać odwołania do obiektów COM  
  
1.  Na **projektu** menu, wybierz **Dodaj odwołanie** , a następnie kliknij przycisk **COM** karty w oknie dialogowym.  
  
2.  Wybierz składnik, który ma być używany z listy obiektów COM.  
  
3.  Aby ułatwić dostęp do zestawu międzyoperacyjnego, Dodaj `Imports` instrukcji na początku klasę lub moduł, w którym będzie używać obiektu COM. Na przykład poniższy przykładowy kod importuje przestrzeń nazw `INKEDLib` dla obiektów, do którego odwołuje się `Microsoft InkEdit Control 1.0` biblioteki.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Aby utworzyć zestaw międzyoperacyjny przy użyciu Tlbimp  
  
1.  Dodaj lokalizację Tlbimp do ścieżki wyszukiwania, jeśli nie jest już częścią ścieżki wyszukiwania i nie jesteś obecnie w katalogu, w którym znajduje się.  
  
2.  Wywołanie Tlbimp z wiersza polecenia, podając następujące informacje:  
  
    -   Nazwa i lokalizacja biblioteki DLL zawierającej biblioteki typów  
  
    -   Nazwa i lokalizacja przestrzeni nazw rozmieszczenia danych  
  
    -   Nazwy i lokalizacji docelowej zestawu międzyoperacyjnego  
  
     Poniższy kod stanowi przykład:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp służy do tworzenia zestawy międzyoperacyjne dla biblioteki typów, nawet w przypadku obiektów COM wyrejestrowany. Jednak z obiektami COM odwołuje się zestawy międzyoperacyjne musi być poprawnie zarejestrowany na komputerze, gdy są do użycia. Obiekt COM można zarejestrować za pomocą narzędzia Regsvr32 zawarte w systemie operacyjnym Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (Importer biblioteki typów)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (Eksporter biblioteki typów)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Wskazówki: Wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Problemów związanych ze współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Imports — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
