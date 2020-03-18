---
title: -warn (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 5b05e944a37e16fc1fcc422271be00c09a271a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602407"
---
# <a name="-warn-c-compiler-options"></a>-warn (Opcje kompilatora C#)
Opcja **-warn** określa poziom ostrzeżenia dla kompilatora do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Poziom ostrzeżenia, który ma być wyświetlany dla kompilacji: Niższe liczby pokazują tylko ostrzeżenia o wysokim stopniu ważności; wyższe liczby wyświetlają więcej ostrzeżeń. Prawidłowe wartości to 0-4:  
  
|Poziom ostrzeżenia|Znaczenie|  
|-------------------|-------------|  
|0|Wyłącza emisję wszystkich komunikatów ostrzegawczych.|  
|1|Wyświetla poważne komunikaty ostrzegawcze.|  
|2|Wyświetla ostrzeżenia poziomu 1 oraz niektóre, mniej poważne ostrzeżenia, takie jak ostrzeżenia dotyczące ukrywania elementów członkowskich klasy.|  
|3|Wyświetla ostrzeżenia poziomu 2 oraz niektóre, mniej poważne ostrzeżenia, takie jak ostrzeżenia `true` dotyczące `false`wyrażeń, które zawsze oceniają lub .|  
|4 (domyślnie)|Wyświetla wszystkie ostrzeżenia poziomu 3 oraz ostrzeżenia informacyjne.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje o błędzie lub ostrzeżeniu, można wyszukać kod błędu w indeksie pomocy. Aby uzyskać inne sposoby uzyskiwania informacji o błędzie lub ostrzeżeniu, zobacz [Błędy kompilatora Języka C#.](../compiler-messages/index.md)  
  
 Użyj [-warnaserror,](./warnaserror-compiler-option.md) aby traktować wszystkie ostrzeżenia jako błędy. Użyj [-nowarn,](./nowarn-compiler-option.md) aby wyłączyć niektóre ostrzeżenia.  
  
 **-w** jest krótką formą **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Zmodyfikuj właściwość **Poziom ostrzeżenia.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Skompiluj `in.cs` i mają kompilator wyświetlać tylko ostrzeżenia poziomu 1:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
