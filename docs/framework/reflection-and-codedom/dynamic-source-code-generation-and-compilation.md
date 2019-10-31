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
ms.openlocfilehash: a7e341bb5bfb5b4648a222409951275169a29b79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130254"
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dynamiczne generowanie i kompilacja kodu źródłowego
.NET Framework obejmuje mechanizm o nazwie Code Document Object Model (CodeDOM), który umożliwia deweloperom programów, które emitują kod źródłowy w celu generowania kodu źródłowego w wielu językach programowania w czasie wykonywania, na podstawie jednego modelu, który reprezentuje kod do renderowania.  
  
 Aby reprezentować kod źródłowy, elementy CodeDOM są połączone ze sobą, aby utworzyć strukturę danych znaną jako wykres CodeDOM, który modeluje strukturę pewnego kodu źródłowego.  
  
 Przestrzeń nazw `System.CodeDom` definiuje typy, które mogą reprezentować logiczną strukturę kodu źródłowego niezależnie od określonego języka programowania. Przestrzeń nazw `System.CodeDom.Compiler` definiuje typy do generowania kodu źródłowego z wykresów CodeDOM i zarządzania kompilacją kodu źródłowego w obsługiwanych językach. Dostawcy lub deweloperzy kompilatora mogą rozciągnąć zestaw obsługiwanych języków.  
  
 Modelowanie kodu źródłowego niezależne od języka może być przydatne, gdy program musi wygenerować kod źródłowy dla modelu programu w wielu językach lub dla nieokreślonego języka docelowego. Na przykład niektórzy projektanci używają języka CodeDOM jako interfejsu abstrakcji języka do tworzenia kodu źródłowego w prawidłowym języku programowania, jeśli dostępna jest obsługa języka CodeDOM.  
  
 .NET Framework obejmuje generatory kodu i kompilatory kodu dla <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>i <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie modelu CodeDOM](using-the-codedom.md)  
 Opisuje typowe zastosowania i demonstruje Tworzenie prostego grafu obiektów przy użyciu CodeDOM.  
  
 [Generowanie kodu źródłowego i kompilowanie programu z wykresu CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Opisuje sposób generowania kodu źródłowego i kompilowania wygenerowanego kodu z kompilatorem zewnętrznym przy użyciu klas zdefiniowanych w przestrzeni nazw `System.CodeDom.Compiler`.  
  
 [Instrukcje: tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM](how-to-create-an-xml-documentation-file-using-codedom.md)  
 Opisuje, jak używać CodeDOM do generowania kodu za pomocą komentarzy dokumentacji XML i kompilowania wygenerowanego kodu w celu utworzenia danych wyjściowych dokumentacji XML.  
  
 [Instrukcje: tworzenie klasy za pomocą modelu CodeDOM](how-to-create-a-class-using-codedom.md)  
 Opisuje, jak używać CodeDOM do wygenerowania klasy zawierającej pola, właściwości, metodę, Konstruktor i punkt wejścia.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.CodeDom>  
 Definiuje elementy reprezentujące elementy kodu w językach programowania przeznaczonych dla środowiska uruchomieniowego języka wspólnego.  
  
 <xref:System.CodeDom.Compiler>  
 Definiuje interfejsy do generowania i kompilowania kodu w czasie wykonywania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zwięzłe odwołanie CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))  
 Umożliwia deweloperom znalezienie elementów CodeDOM, które reprezentują elementy kodu źródłowego.
