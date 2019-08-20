---
title: -Optymalizuj (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606601"
---
# <a name="-optimize-c-compiler-options"></a>-Optymalizuj (C# opcje kompilatora)
Opcja **-Optimize** włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajny.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 **-Optymalizuj** również informuje środowisko uruchomieniowe języka wspólnego, aby zoptymalizować kod w czasie wykonywania.  
  
 Optymalizacje są domyślnie wyłączone. Określ **-Optimize +** , aby włączyć optymalizacje.  
  
 Podczas kompilowania modułu, który ma być używany przez zestaw, należy użyć tych samych ustawień, co w przypadku zestawu.  
  
 **-o** jest krótką formą **optymalizacji**.  
  
 Istnieje możliwość połączenia opcji **-Optimize** i [-Debug](./debug-compiler-option.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Zmodyfikuj właściwość **Optimize Code** .  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t2.cs` i Włącz optymalizacje kompilatora:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
