---
title: "Dynamiczne generowanie i kompilacja kodu źródłowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535a60aa1a174319a4db3403a64c3998784bbb58
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="dynamic-source-code-generation-and-compilation"></a>Dynamiczne generowanie i kompilacja kodu źródłowego
Mechanizm wywołuje kod Document Object Model (CodeDOM), który umożliwia deweloperom programów, które Emituj kod źródłowy do generowania kodu źródłowego w wielu języków programowania, w czasie wykonywania, oparte na jednym modelu, który reprezentuje kod zawiera programu .NET Framework do renderowania.  
  
 Do reprezentowania kodu źródłowego, CodeDOM elementy są połączone ze sobą do tworzenia struktury danych, nazywane wykresu CodeDOM modele struktury kodu źródłowego.  
  
 `System.CodeDom` Przestrzeni nazw definiuje typy reprezentujące struktury logicznej kodu źródłowego, niezależnie od określonego języka programowania. `System.CodeDom.Compiler` Przestrzeni nazw określa typy generowanie kodu źródłowego z wykresu CodeDOM i zarządzania nimi kompilacji kodu źródłowego w obsługiwanych językach. Dostawcom kompilatora i deweloperzy mogą rozszerzać zestaw obsługiwanych języków.  
  
 Modelowanie kodu źródłowego niezależnego od języka może być przydatna, gdy program wymaga do generowania kodu źródłowego dla modelu programu w wielu językach lub niepewne języka docelowego. Na przykład niektóre projektanci używali modelu CodeDOM jako interfejs abstrakcji języka aby wygenerować kod źródłowy w języku programowania, jeśli dostępna jest obsługa CodeDOM dla języka.  
  
 .NET Framework obejmuje generatory kodu i kompilatory kodu dla <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, i <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie modelu CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 W tym artykule opisano typowe zastosowania i pokazano tworzenie wykres prostych obiektów przy użyciu modelu CodeDOM.  
  
 [Generowanie kodu źródłowego i kompilowanie programu z wykresu CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Opisuje sposób generowania kodu źródłowego i kompilowania wygenerowanego kodu z zewnętrznego kompilatorem przy użyciu klas zdefiniowanych w `System.CodeDom.Compiler` przestrzeni nazw.  
  
 [Instrukcje: tworzenie pliku dokumentacji XML przy użyciu modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 Informacje dotyczące używania CodeDOM do generowania kodu przy użyciu komentarze dokumentacji XML i kompilowania wygenerowanego kodu tak, aby tworzy dane wyjściowe dokumentacji XML.  
  
 [Instrukcje: tworzenie klasy za pomocą modelu CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 Informacje dotyczące używania CodeDOM do generowania klasy zawierające pola, właściwości, metody, konstruktora i punktu wejścia.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.CodeDom>  
 Definiuje elementy, które reprezentują elementy kodu w językach programowania kierowanych środowisko uruchomieniowe języka wspólnego.  
  
 <xref:System.CodeDom.Compiler>  
 Definiuje interfejs Generowanie i kompilowanie kodu w czasie wykonywania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Krótki przewodnik codeDOM](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 Umożliwia szybkie dla deweloperów znaleźć elementy CodeDOM, które reprezentują elementy kodu źródłowego.
