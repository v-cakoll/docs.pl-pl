---
title: Typ &#39; &lt;typename&gt; &#39; nie jest zdefiniowana
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 8e303a9ac6529fbbc818c94497a16463897fb0c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496130"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Typ &#39; &lt;typename&gt; &#39; nie jest zdefiniowana
Wykonywanie instrukcji wprowadził odwołanie do typu, który nie został zdefiniowany. Można zdefiniować typ w instrukcji deklaracji takich jak `Enum`, `Structure`, `Class`, lub `Interface`.  
  
 **Identyfikator błędu:** BC30002  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że w definicji typu i odwołanie, zarówno używają tej samej pisowni.  
  
-   Upewnij się, że definicji typu jest dostępny do odwołania. Na przykład, jeśli typ znajduje się w innym module i został zadeklarowany `Private`, Przenieś definicji typu modułu odwołujący się lub Zadeklaruj go `Public`.  
  
-   Upewnij się, że obszar nazw tego typu nie jest ponownie zdefiniować w obrębie projektu. Jeśli tak jest, należy użyć `Global` — słowo kluczowe pełnej nazwy typu. Na przykład, jeśli projektu definiuje obszar nazw o nazwie `System`, <xref:System.Object?displayProperty=nameWithType> typu nie można uzyskać dostępu, chyba że jest to w pełni kwalifikowaną nazwą zawierającą `Global` — słowo kluczowe: `Global.System.Object`.  
  
-   Jeśli typ jest zdefiniowany, ale obiekt biblioteki lub bibliotekę typów, w którym jest zdefiniowany, nie jest zarejestrowany w Visual Basic, kliknij kolejno pozycje **Dodaj odwołanie** na **projektu** menu, a następnie wybierz odpowiedni obiekt biblioteki lub bibliotekę typów.  
  
-   Upewnij się, że typ w zestawie, który jest częścią profilu docelowej platformy .NET Framework. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z celem błędy programu .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Zobacz także
- [Przestrzenie nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)
