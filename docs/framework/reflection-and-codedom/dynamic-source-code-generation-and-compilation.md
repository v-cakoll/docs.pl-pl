---
title: Dynamiczne generowanie i kompilacja kodu źródłowego
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90b4214e244bc1f9c5f8e71782e604bd6c7b619
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582596"
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dynamiczne generowanie i kompilacja kodu źródłowego
Program .NET Framework zawiera do tego mechanizm nazywany kodu Document Object Model (CodeDOM) umożliwia deweloperom programy, które emitują kod źródłowy do generowania kodu źródłowego w wielu językach programowania, w czasie wykonywania, oparty na jednym modelu, który reprezentuje kod do renderowania.  
  
 Do reprezentowania kodem źródłowym, elementami CodeDOM są połączone ze sobą w celu utworzenia struktury danych, nazywane wykresu CodeDOM, który modeluje struktury kodu źródłowego.  
  
 `System.CodeDom` Przestrzeni nazw definiuje typy, które mogą reprezentować logicznej struktury kodu źródłowego, niezależnie od określonego języka programowania. `System.CodeDom.Compiler` Przestrzeni nazw definiuje typy, generowanie kodu źródłowego z wykresu CodeDOM i zarządzania nimi kompilacja kodu źródłowego w obsługiwanych językach. Kompilator dostawców lub deweloperów, można rozszerzyć zbiór języków.  
  
 Modelowanie kodu źródłowego niezależnego od języka mogą być przydatne, gdy program wymaga wygenerować kod źródłowy dla modelu programu, w wielu językach lub niepewne języka docelowego. Na przykład niektóre projektantów umożliwia CodeDOM jako interfejs abstrakcji języka generuje kod źródłowy w języku programowania, jeśli dostępna jest obsługa CodeDOM dla języka.  
  
 Program .NET Framework zawiera generatorów kodu i kompilatory kodu <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, i <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 W tym artykule opisano typowe zastosowania i pokazuje, tworzenia grafu prostego obiektu za pomocą modelu CodeDOM.  
  
 [Generowanie kodu źródłowego i kompilacja programu z wykresu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 W tym artykule opisano sposób generowania kodu źródłowego i kompilowania wygenerowanego kodu za pomocą zewnętrznego kompilatora przy użyciu klas zdefiniowanych w `System.CodeDom.Compiler` przestrzeni nazw.  
  
 [Instrukcje: tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 W tym artykule opisano, jak za pomocą modelu CodeDOM generowanie kodu za pomocą komentarzy dokumentacji XML i kompilowania wygenerowanego kodu, aby tworzy dane wyjściowe dokumentacji XML.  
  
 [Instrukcje: tworzenie klasy za pomocą modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 W tym artykule opisano, jak wygenerować klasę, zawierający pola, właściwości, metody, Konstruktor i punktu wejścia za pomocą modelu CodeDOM.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.CodeDom>  
 Definiuje elementy, które reprezentują elementy kodu w językach programowania przeznaczonych środowiska uruchomieniowego języka wspólnego.  
  
 <xref:System.CodeDom.Compiler>  
 Definiuje interfejsów Generowanie i kompilowanie kodu w czasie wykonywania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [CodeDOM — podręczny wykaz](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 Umożliwia szybkie dla deweloperów można znaleźć elementów CodeDOM, które reprezentują elementy kodu źródłowego.
