---
title: Dokumentowanie kodu za pomocą XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 645dd4a8a9d1c78fd54f0f31ad0efd772b671d39
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Dokumentowanie kodu za pomocą XML (Visual Basic)
W języku Visual Basic można udokumentować kod za pomocą XML  
  
## <a name="xml-documentation-comments"></a>Komentarze dokumentacji XML  
 Visual Basic zapewnia prosty sposób na automatyczne tworzenie dokumentacji XML dla projektów. Można automatycznie generować szkielet XML dla typów i członków, a następnie podaj podsumowania, dokumentacja opisową dla każdego parametru i inne uwagi. W przypadku odpowiedniej konfiguracji dokumentacji XML jest automatycznie wysyłanego do pliku XML z taką samą nazwę jak projektu i rozszerzenie .xml. Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 Plik XML można używane lub w przeciwnym razie manipulować w formacie XML. Ten plik znajduje się w tym samym katalogu co plik .exe lub .dll danych wyjściowych projektu.  
  
 Plik dokumentacji XML, który rozpoczyna się od `'''`. Przetwarzanie komentarze ma pewne ograniczenia:  
  
-   Dokumentację musi być poprawnie sformułowanym XML. Jeśli plik XML nie jest poprawnie sformułowany, generowania ostrzeżeń i pliku dokumentacji zawiera komentarz informujący o tym, że wystąpił błąd podczas.  
  
-   Deweloperzy mogą tworzyć własne zestawu tagów. Brak zalecanych zbiór znaczników (zobacz "Sekcje pokrewne" w tym temacie). Niektóre zalecane znaczniki mają specjalne znaczenie:  
  
    -   \<Param > tag jest używany do opisywania parametrów. Jeśli używana, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry są opisane w dokumentacji. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie.  
  
    -   `cref` Atrybut może zostać dołączony do żadnych znacznik w celu zapewnienia odwołania do elementu kodu. Kompilator sprawdza, czy istnieje tego elementu kodu. Jeśli weryfikacja zakończy się niepowodzeniem, kompilator generuje ostrzeżenie. Kompilator również szanuje żadnego `Imports` instrukcje podczas wyszukiwania dla typu opisanego w `cref` atrybutu.  
  
    -   \<Podsumowania > tag jest używany przez funkcję IntelliSense w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji na temat tworzenia pliku XML z komentarzy do dokumentacji zobacz następujące tematy:  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Przetwarzanie pliku XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Instrukcje: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Narzędzia XML w Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji za pomocą języka Visual Basic](../../../visual-basic/developing-apps/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
