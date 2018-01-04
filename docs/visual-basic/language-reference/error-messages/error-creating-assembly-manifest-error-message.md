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
ms.openlocfilehash: 5e88d28ef787eb57b71d94f4ee51c09e9751dbff
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wywołuje konsolidator zestawów (znanej także jako Alink Al.exe), można wygenerować zestawu z manifestu. Konsolidator zgłosił błąd w fazie emisji wstępnego tworzenia zestawu.  
  
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
