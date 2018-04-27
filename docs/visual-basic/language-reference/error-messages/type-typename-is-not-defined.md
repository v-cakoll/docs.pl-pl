---
title: Typ &#39; &lt;typename&gt; &#39; nie jest zdefiniowany
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7c3efbcabf1e40c7f550b5f54d16e697561cf82c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Typ &#39; &lt;typename&gt; &#39; nie jest zdefiniowany
Instrukcja wprowadził odwołanie do typu, który nie został zdefiniowany. Można zdefiniować typu w instrukcji deklaracji takich jak `Enum`, `Structure`, `Class`, lub `Interface`.  
  
 **Identyfikator błędu:** BC30002  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że definicji typu i jego odwołania oba rozwiązania używają tej samej pisowni.  
  
-   Upewnij się, że definicja typu jest dostępny do odwołania. Na przykład, jeśli typ znajduje się w innym module i została zadeklarowana `Private`, Przenieś definicji typu modułu odwołujący się lub Zadeklaruj `Public`.  
  
-   Upewnij się, że obszar nazw tego typu nie zostało ponownie zdefiniowane w ramach projektu. Jeśli tak jest, użyj `Global` — słowo kluczowe pełnej nazwy typu. Na przykład, jeśli projekt definiuje obszar nazw o nazwie `System`, <xref:System.Object?displayProperty=nameWithType> nie można uzyskać dostępu do typu, o ile nie jest w pełni kwalifikowanej z `Global` — słowo kluczowe: `Global.System.Object`.  
  
-   Jeśli typ jest zdefiniowany, ale obiekt biblioteki lub bibliotekę typów, w którym jest zdefiniowany nie jest zarejestrowany w Visual Basic, kliknij pozycję **Dodaj odwołanie** na **projektu** menu, a następnie wybierz odpowiedni obiekt biblioteki lub biblioteki typów.  
  
-   Upewnij się, że typ jest w zestawie, do którego jest częścią docelowej profilu .NET Framework. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z błędami docelowy Framework .NET](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)
