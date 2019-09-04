---
title: Nazwa „<name>" nie została zadeklarowana
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: dfa1d1600c7943e503b4f5ec2e2b8ecd6fbb9fe0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254202"
---
# <a name="name-name-is-not-declared"></a>Nazwa "\<Name >" nie jest zadeklarowana
Instrukcja odwołuje się do elementu programistycznego, ale kompilator nie może odnaleźć elementu o takiej samej nazwie.  
  
 **Identyfikator błędu:** BC30451  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź pisownię nazwy w instrukcji odwołującej. W Visual Basic nie jest rozróżniana wielkość liter, ale każda inna zmiana pisowni jest traktowana jako zupełnie inna nazwa. Należy zauważyć, że podkreślenie`_`() jest częścią nazwy i w związku z tym jest częścią pisowni.  
  
2. Sprawdź, czy masz operator dostępu do elementu członkowskiego (`.`) między obiektem a jego składową. <xref:System.Windows.Forms.TextBox> Na przykład jeśli masz kontrolkę o nazwie `TextBox1`, aby uzyskać dostęp do <xref:System.Windows.Forms.TextBoxBase.Text%2A> jej właściwości, należy `TextBox1.Text`wpisać. Jeśli zamiast tego wpiszesz `TextBox1Text`, utworzona zostanie inna nazwa.  
  
3. Jeśli pisownia jest poprawna i składnia dowolnego dostępu do elementu członkowskiego obiektu jest poprawna, sprawdź, czy element został zadeklarowany. Aby uzyskać więcej informacji, zobacz [elementy zadeklarowane](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Jeśli element programowania został zadeklarowany, sprawdź, czy znajduje się w zakresie. Jeśli instrukcja odwołująca znajduje się poza regionem deklarującym element programowania, może być konieczne zakwalifikowanie nazwy elementu. Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).  

5. Jeśli nie używasz w pełni kwalifikowanego typu lub typu i nazwy elementu członkowskiego (na przykład kod odwołuje się do właściwości jako `MethodInfo.Name` " `System.Reflection.MethodInfo.Name`zamiast"), Dodaj [instrukcję Imports](../statements/imports-statement-net-namespace-and-type.md).

6. Jeśli próbujesz skompilować projekt w stylu zestawu SDK (projekt z \*plikiem. vbproj, który rozpoczyna się od wiersza `<Project Sdk="Microsoft.NET.Sdk">`), a komunikat o błędzie dotyczy typu lub elementu członkowskiego zestawu Microsoft. VisualBasic. dll, skonfiguruj aplikację do Kompiluj z odwołaniem do biblioteki środowiska uruchomieniowego Visual Basic. Domyślnie podzestaw biblioteki jest osadzony w zestawie w projekcie w stylu zestawu SDK.

   Na przykład następujący przykład nie zostanie skompilowany, ponieważ <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> nie można odnaleźć metody. Nie jest on osadzony w podzbiorze środowiska uruchomieniowego Visual Basic dołączonego do aplikacji.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   Aby rozwiązać ten problem, Dodaj `<VBRuntime>Default</VBRuntime>` element do sekcji projekty `<PropertyGroup>` , jak pokazano w poniższym pliku projektu Visual Basic.

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Zobacz także

- [Deklaracje i stałe — podsumowanie](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Konwencje nazewnictwa Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
