---
title: -warnaserror (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a341fe9760d7fdb0e4df7046cf356e550b4adb9
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (opcje kompilatora C#)
**- Warnaserror +** opcji traktuje wszystkie ostrzeżenia jako błędy  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Uwagi  
 Komunikaty, które zazwyczaj będzie zgłaszane jako ostrzeżenia zamiast tego są raportowane klientowi jako błędy, a proces kompilacji zostało zatrzymane (żadne dane wyjściowe są tworzone pliki).  
  
 Domyślnie **- warnaserror —** obowiązują, co powoduje, że ostrzeżenia dotyczące zapobiega generowaniu pliku wyjściowego. **-warnaserror**, która jest taka sama jak **- warnaserror +**, powoduje, że ostrzeżenia, które będą traktowane jako błędy.  
  
 Opcjonalnie Jeśli chcesz tylko kilka konkretne ostrzeżenia, które będą traktowane jako błędy mogą określić rozdzielana przecinkami lista numerów ostrzeżeń, które mają być traktowane jako błędy.  
  
 Użyj [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) określa poziom ostrzeżeń, które mają kompilatora do wyświetlenia. Użyj [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) Aby wyłączyć określone ostrzeżenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Modyfikowanie **Traktuj ostrzeżenia jako błędy** właściwości.  
  
 Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i mieć kompilatora wyświetlane nie ostrzeżenia:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
