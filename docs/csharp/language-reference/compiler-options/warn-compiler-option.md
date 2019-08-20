---
title: -warn (C# opcje kompilatora)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602407"
---
# <a name="-warn-c-compiler-options"></a>-warn (C# opcje kompilatora)
Opcja **-warn** określa poziom ostrzeżeń dla kompilatora, który ma być wyświetlany.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Poziom ostrzeżeń, który ma być wyświetlany dla kompilacji: Niższe numery pokazują tylko ostrzeżenia o wysokiej ważności; wyższe liczby zawierają więcej ostrzeżeń. Prawidłowe wartości to 0-4:  
  
|Poziom ostrzeżeń|Znaczenie|  
|-------------------|-------------|  
|0|Wyłącza emisję wszystkich komunikatów ostrzegawczych.|  
|1|Wyświetla poważne komunikaty ostrzegawcze.|  
|2|Wyświetla ostrzeżenia poziomu 1 i pewne mniej surowe ostrzeżenia, takie jak ostrzeżenia dotyczące ukrywania elementów członkowskich klasy.|  
|3|Wyświetla ostrzeżenia poziomu 2 oraz pewne mniej surowe ostrzeżenia, takie jak ostrzeżenia dotyczące wyrażeń, które zawsze są oceniane do `true` lub `false`.|  
|4 (wartość domyślna)|Wyświetla wszystkie ostrzeżenia poziomu 3 i ostrzeżenia informacyjne.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje o błędzie lub ostrzeżeniu, można wyszukać kod błędu w indeksie pomocy. Aby uzyskać informacje dotyczące błędu lub ostrzeżenia, zobacz [ C# błędy kompilatora](../compiler-messages/index.md).  
  
 Użyj opcji [-warnaserror —](./warnaserror-compiler-option.md) , aby traktować wszystkie ostrzeżenia jako błędy. Użyj [-nowarn](./nowarn-compiler-option.md) , aby wyłączyć niektóre ostrzeżenia.  
  
 **-w** jest krótką formą **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Zmodyfikuj właściwość **poziom ostrzeżeń** .  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i czy kompilator wyświetla tylko ostrzeżenia poziomu 1:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
