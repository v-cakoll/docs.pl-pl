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
ms.openlocfilehash: 7379bac07de9b78369d3742fa3288f6fea6a573f
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544982"
---
# <a name="compile-and-generate-dynamic-source-code"></a>Kompiluj i Generuj dynamiczny kod źródłowy

.NET Framework obejmuje mechanizm o nazwie Code Document Object Model (CodeDOM), który umożliwia deweloperom programów, które emitują kod źródłowy w celu generowania kodu źródłowego w wielu językach programowania w czasie wykonywania, na podstawie jednego modelu, który reprezentuje kod do renderowania.  
  
Aby reprezentować kod źródłowy, elementy CodeDOM są połączone ze sobą, aby utworzyć strukturę danych znaną jako wykres CodeDOM, który modeluje strukturę pewnego kodu źródłowego.  
  
Przestrzeń nazw <xref:System.CodeDom?displayProperty=fullName> definiuje typy, które mogą reprezentować logiczną strukturę kodu źródłowego niezależnie od określonego języka programowania. Przestrzeń nazw <xref:System.CodeDom.Compiler?displayProperty=fullName> definiuje typy do generowania kodu źródłowego z wykresów CodeDOM i zarządzania kompilacją kodu źródłowego w obsługiwanych językach. Dostawcy lub deweloperzy kompilatora mogą rozciągnąć zestaw obsługiwanych języków.  
  
Modelowanie kodu źródłowego niezależne od języka może być przydatne, gdy program musi wygenerować kod źródłowy dla modelu programu w wielu językach lub dla nieokreślonego języka docelowego. Na przykład niektórzy projektanci używają języka CodeDOM jako interfejsu abstrakcji języka do tworzenia kodu źródłowego w prawidłowym języku programowania, jeśli dostępna jest obsługa języka CodeDOM.  
  
.NET Framework obejmuje generatory kodu i kompilatory kodu dla <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>i <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>W tej sekcji

- [Używanie modelu CodeDOM](using-the-codedom.md)

  Opisuje typowe zastosowania i demonstruje Tworzenie prostego grafu obiektów przy użyciu CodeDOM.  
  
- [Generowanie kodu źródłowego i kompilowanie programu z wykresu CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md)  

  Opisuje sposób generowania kodu źródłowego i kompilowania wygenerowanego kodu z kompilatorem zewnętrznym przy użyciu klas zdefiniowanych w przestrzeni nazw `System.CodeDom.Compiler`.  
  
- [Instrukcje: tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM](how-to-create-an-xml-documentation-file-using-codedom.md)  

  Opisuje, jak używać CodeDOM do generowania kodu za pomocą komentarzy dokumentacji XML i kompilowania wygenerowanego kodu w celu utworzenia danych wyjściowych dokumentacji XML.  
  
- [Instrukcje: tworzenie klasy za pomocą modelu CodeDOM](how-to-create-a-class-using-codedom.md)  

  Opisuje, jak używać CodeDOM do wygenerowania klasy zawierającej pola, właściwości, metodę, Konstruktor i punkt wejścia.  
  
## <a name="reference"></a>Tematy pomocy  

- <xref:System.CodeDom>  

  Definiuje elementy reprezentujące elementy kodu w językach programowania przeznaczonych dla środowiska uruchomieniowego języka wspólnego.  
  
- <xref:System.CodeDom.Compiler>  

  Definiuje interfejsy do generowania i kompilowania kodu w czasie wykonywania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

- [Szybka dokumentacja CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) umożliwia deweloperom znalezienie elementów CodeDOM, które reprezentują elementy kodu źródłowego.
