---
title: "Porady: użycie funkcji dokumentacji XML (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb647a275a5cd5fac2316706591440d9792861b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>Porady: użycie funkcji dokumentacji XML (Przewodnik programowania w języku C#)
Poniższy przykład zawiera ogólne omówienie typu, który został udokumentowany.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **Ten plik XML został wygenerowany z powyższego przykładu kodu.**  
**\<? wersji xml = "1.0"? >**  
**\<doc >**  
 **\<zestaw >**  
 **\<nazwa > xmlsample \< /name >**  
 **\</ Assembly >**  
 **\<elementy członkowskie >**  
 **\<Nazwa elementu = "T:SomeClass" >**  
 **\<podsumowania >**  
 **Tutaj należy wstawić poziomu dokumentacji podsumowania klasy.  \< /summary >**  
 **\<Remarks >**  
 **Komentarze dłużej może być skojarzony z typu lub elementu członkowskiego**  
 **za pomocą tagu uwagi \< /remarks >**  
 **\</Member >**  
 **\<element członkowski name="F:SomeClass.m_Name" >**  
 **\<podsumowania >**  
 **Magazyn dla właściwości nazwy \< /summary >**  
 **\</Member >**  
 **\<Nazwa elementu = "M:SomeClass. #ctor" >**  
 **\<Podsumowanie > konstruktora klasy.  \< /summary >**  
 **\</Member >**  
 **\<element członkowski name="M:SomeClass.SomeMethod(System.String)" >**  
 **\<podsumowania >**  
 **Opis SomeMethod.  \< /summary >**  
 **\<param name = "s" > tutaj opis parametru s\</param >**  
 **\<SeeAlso cref="T:System.String" >**  
 **Atrybut cref dowolny znacznik służy do odwołania, typu lub elementu członkowskiego**  
 **i kompilator będzie sprawdzać, czy istnieje odwołanie. \</seealso >**  
 **\</Member >**  
 **\<element członkowski name="M:SomeClass.SomeOtherMethod" >**  
 **\<podsumowania >**  
 **Innej metody.  \< /summary >**  
 **\<Zwraca >**  
 **Za pomocą tagu zwraca opisano zwracanych wyników.  \< /returns >**  
 **\<SeeAlso cref="M:SomeClass.SomeMethod(System.String)" >**  
 **Zwróć uwagę na atrybut cref, aby odwołać określonej metody \</seealso >**  
 **\</Member >**  
 **\<element członkowski name="M:SomeClass.Main(System.String[])" >**  
 **\<podsumowania >**  
 **Punkt wejścia dla aplikacji.**  
 **\</ summary >**  
 **\<param name = "args" > Lista argumentów wiersza polecenia\</param >**  
 **\</Member >**  
 **\<element członkowski name="P:SomeClass.Name" >**  
 **\<podsumowania >**  
 **Nazwa właściwości  \< /summary >**  
 **\<wartość >**  
 **Wartość tagu jest używany do opisu wartość właściwości \< /value >**  
 **\</Member >**  
 **\</members >**  
**\</ doc >**   
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować w przykładzie, wpisz następujące polecenie w wierszu:  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Spowoduje to utworzenie pliku XML XMLsample.xml, które można wyświetlić w przeglądarce lub za pomocą polecenia typu.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Plik dokumentacji XML rozpoczyna się od lokalizacje. Podczas tworzenia nowego projektu kreatorów umieść starter lokalizacje wiersze w automatycznie. Przetwarzanie komentarze ma pewne ograniczenia:  
  
-   Dokumentację musi być poprawnie sformułowanym XML. Jeśli plik XML nie jest poprawnie sformułowany, generowania ostrzeżeń i pliku dokumentacji będzie zawierać komentarz z informacją, że wystąpił błąd podczas.  
  
-   Deweloperzy mogą tworzyć własne zestawu tagów. Brak zalecanych zbiór znaczników (patrz sekcja dalsze informacje). Niektóre zalecane znaczniki mają specjalne znaczenie:  
  
    -   \<Param > tag jest używany do opisywania parametrów. Jeśli używana, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry są opisane w dokumentacji. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.  
  
    -   `cref` Atrybut może zostać dołączony do żadnych znacznik w celu zapewnienia odwołania do elementu kodu. Kompilator będzie Sprawdź, czy istnieje tego elementu kodu. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie. Kompilator szanuje żadnego `using` instrukcje podczas wyszukiwania typu opisanego w `cref` atrybutu.  
  
    -   \<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.  
  
        > [!NOTE]
        >  Plik XML nie zapewnia pełne informacje dotyczące typu i elementów członkowskich (na przykład go nie zawiera żadnych informacji o typie). Aby uzyskać pełne informacje dotyczące typu lub elementu członkowskiego, plik dokumentacji musi być używany razem odbicia na rzeczywisty typ lub element członkowski.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
