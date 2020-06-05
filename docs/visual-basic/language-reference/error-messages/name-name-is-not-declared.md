---
title: Nazwa „<name>" nie została zadeklarowana
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 6fa4639b97e4314d8752ae520e94a58a189b7cbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397171"
---
# <a name="name-name-is-not-declared"></a>Nazwa „\<name>" nie została zadeklarowana
Instrukcja odwołuje się do elementu programistycznego, ale kompilator nie może odnaleźć elementu o takiej samej nazwie.  
  
 **Identyfikator błędu:** BC30451  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź pisownię nazwy w instrukcji odwołującej. W Visual Basic nie jest rozróżniana wielkość liter, ale każda inna zmiana pisowni jest traktowana jako zupełnie inna nazwa. Należy zauważyć, że podkreślenie ( `_` ) jest częścią nazwy i w związku z tym jest częścią pisowni.  
  
2. Sprawdź, czy masz operator dostępu do elementu członkowskiego ( `.` ) między obiektem a jego składową. Na przykład jeśli masz <xref:System.Windows.Forms.TextBox> kontrolkę o nazwie `TextBox1` , aby uzyskać dostęp do jej właściwości, należy <xref:System.Windows.Forms.TextBoxBase.Text%2A> wpisać `TextBox1.Text` . Jeśli zamiast tego wpiszesz `TextBox1Text` , utworzona zostanie inna nazwa.  
  
3. Jeśli pisownia jest poprawna i składnia dowolnego dostępu do elementu członkowskiego obiektu jest poprawna, sprawdź, czy element został zadeklarowany. Aby uzyskać więcej informacji, zobacz [elementy zadeklarowane](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Jeśli element programowania został zadeklarowany, sprawdź, czy znajduje się w zakresie. Jeśli instrukcja odwołująca znajduje się poza regionem deklarującym element programowania, może być konieczne zakwalifikowanie nazwy elementu. Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).  

5. Jeśli nie używasz w pełni kwalifikowanego typu lub typu i nazwy elementu członkowskiego (na przykład kod odwołuje się do właściwości jako " `MethodInfo.Name` zamiast" `System.Reflection.MethodInfo.Name` ), Dodaj [instrukcję Imports](../statements/imports-statement-net-namespace-and-type.md).

6. Jeśli próbujesz skompilować projekt w stylu zestawu SDK (projekt z \* plikiem. vbproj, który zaczyna się od wiersza `<Project Sdk="Microsoft.NET.Sdk">` ), a komunikat o błędzie dotyczy typu lub elementu członkowskiego zestawu Microsoft. VisualBasic. dll, skonfiguruj aplikację do kompilowania z odwołaniem do biblioteki środowiska uruchomieniowego Visual Basic. Domyślnie podzestaw biblioteki jest osadzony w zestawie w projekcie w stylu zestawu SDK.

   Na przykład następujący przykład nie zostanie skompilowany, ponieważ <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> nie można odnaleźć metody. Nie jest on osadzony w podzbiorze środowiska uruchomieniowego Visual Basic dołączonego do aplikacji.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   Aby rozwiązać ten problem, Dodaj `<VBRuntime>Default</VBRuntime>` element do `<PropertyGroup>` sekcji projekty, jak pokazano w poniższym pliku projektu Visual Basic.

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Zobacz też

- [Deklaracje i stałe — podsumowanie](../keywords/declarations-and-constants-summary.md)
- [Visual Basic — Konwencje nazewnictwa](../../programming-guide/program-structure/naming-conventions.md)
- [Nazwy zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odwołania do elementów zadeklarowanych](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
