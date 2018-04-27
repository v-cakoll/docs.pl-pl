---
title: 'Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4032bbcbf9924eb5aad4e2cb1a6e74df9a472eca
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;
Kompilator Visual Basic wywołuje konsolidator zestawów (znanej także jako Alink Al.exe), można wygenerować zestawu z manifestu. Konsolidator zgłosił błąd w fazie emisji wstępnego tworzenia zestawu.  
  
 Może to występować, jeśli występują problemy z pliku klucza lub kontener klucza określony. Pełni podpisać zestawu, należy podać prawidłowy plik klucza, który zawiera informacje o klucze publiczne i prywatne. Aby opóźnić Podpisz zestaw, musisz wybrać **opóźnienie tylko znak** pole wyboru i podaj prawidłowy plik klucza, który zawiera informacje o informacje o kluczu publicznym. Klucz prywatny nie jest konieczne, gdy zestaw jest podpisywany z opóźnieniem. Aby uzyskać więcej informacji, zobacz [porady: podpisać zestaw o silnej nazwie](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 **Identyfikator błędu:** BC30140  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). więcej informacji o AL1019 i porady  
  
2.  Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: podpisywanie zestawu silną nazwą](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
