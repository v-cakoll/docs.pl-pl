---
title: Nazwa &#39; &lt;nazwa&gt; &#39; nie została zadeklarowana
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
author: rpetrusha
ms.author: ronpet
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 3f950bd5604fae7c7d48f6898a4514053061fe10
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122810"
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Nazwa &#39; &lt;nazwa&gt; &#39; nie została zadeklarowana
Oświadczenie odnosi się do elementu programistycznego, ale kompilator nie może odnaleźć element o takiej samej nazwie.  
  
 **Identyfikator błędu:** BC30451  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź pisownię nazwy w instrukcji odwołujących się. Visual Basic jest rozróżniana wielkość liter, ale inne zmienność pisowni jest traktowany jako całkowicie inną nazwę. Należy pamiętać, że znak podkreślenia (`_`) jest częścią nazwy i w związku z tym część pisownię.  
  
2. Sprawdź, czy operator dostępu do elementu członkowskiego (`.`) między obiektem i jego elementów członkowskich. Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formantu o nazwie `TextBox1`, aby uzyskać dostęp do jego <xref:System.Windows.Forms.TextBoxBase.Text%2A> właściwość, należy wpisać `TextBox1.Text`. Jeśli zamiast tego wpisz `TextBox1Text`, utworzono inną nazwę.  
  
3. Jeśli składnia dostęp do dowolnego obiektu elementu członkowskiego jest poprawna Pisownia jest poprawna, sprawdź, czy element został zadeklarowany. Aby uzyskać więcej informacji, zobacz [zadeklarowane elementy](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Jeśli zadeklarowano elementu programistycznego, sprawdź, czy są w zakresie. W przypadku instrukcji odwołujących się poza regionem deklarowania elementu programistycznego, może być konieczne kwalifikowania nazwy elementu. Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).  

5. Jeśli nie używasz w pełni kwalifikowany typ lub nazwa typów i elementów członkowskich (na przykład kod odwołuje się do właściwości jako `MethodInfo.Name` zamiast `System.Reflection.MethodInfo.Name`), Dodaj [Imports — instrukcja](../statements/imports-statement-net-namespace-and-type.md).

6. Jeśli chcesz skompilować projekt w stylu zestawu SDK (projektu za pomocą \*pliku .vbproj, który rozpoczyna się od wiersza `<Project Sdk="Microsoft.NET.Sdk">`), a komunikat o błędzie, który odwołuje się do typu lub elementu członkowskiego w zestawie Microsoft.VisualBasic.dll, umożliwia skonfigurowanie aplikacji Skompiluj z odwołaniem do biblioteki środowiska uruchomieniowego Visual Basic. Domyślnie podzbiór biblioteki jest osadzony w swoim zestawie, w projekcie zestawu SDK stylu.

   Na przykład, poniższy przykład nie powiedzie się do kompilacji ponieważ <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> nie można odnaleźć metody. Nie jest zagnieżdżony w podzbiorze środowiska uruchomieniowego Visual Basic, dołączone do aplikacji.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   Aby rozwiązać ten błąd, należy dodać `<VBRuntime>Default</VBRuntime>` element do projektów `<PropertyGroup>` sekcji, co ilustruje poniższy plik projektu języka Visual Basic.

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Zobacz także  

[Deklaracje i stałe — podsumowanie](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
