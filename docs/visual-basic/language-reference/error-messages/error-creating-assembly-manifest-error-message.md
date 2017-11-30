---
title: "Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wywołuje konsolidator zestawów (znanej także jako Alink Al.exe), można wygenerować zestawu z manifestu. Konsolidator zgłosił błąd w fazie emisji wstępnego tworzenia zestawu.  
  
 Może to występować, jeśli występują problemy z pliku klucza lub kontener klucza określony. Pełni podpisać zestawu, należy podać prawidłowy plik klucza, który zawiera informacje o klucze publiczne i prywatne. Aby opóźnić Podpisz zestaw, musisz wybrać **opóźnienie tylko znak** pole wyboru i podaj prawidłowy plik klucza, który zawiera informacje o informacje o kluczu publicznym. Klucz prywatny nie jest konieczne, gdy zestaw jest podpisywany z opóźnieniem. Aby uzyskać więcej informacji, zobacz [porady: podpisać zestawu (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **Identyfikator błędu:** BC30140  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe narzędzia błędy i ostrzeżenia](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) błąd AL1019 bardziej wyjaśnienie i porady  
  
2.  Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: podpisać zestawu (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe (konsolidator zestawów)](https://msdn.microsoft.com/library/c405shex)  
 [Narzędzie Al.exe błędy i ostrzeżenia](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
