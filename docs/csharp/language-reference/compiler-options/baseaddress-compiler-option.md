---
title: -baseaddress (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937211"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (Opcje kompilatora C#)
Opcja **-baseaddress** umożliwia określenie preferowanego adresu podstawowego, pod którym ma zostać załadowana dll. Aby uzyskać więcej informacji o tym, kiedy i dlaczego warto użyć tej opcji, zobacz [Logowanie Larry'ego Ostermana](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Adres podstawowy dla pliku DLL. Ten adres można określić jako liczbę dziesiętną, szesnastkową lub ósemkową.  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy dla dll jest ustawiany przez program runtime wspólnego języka .NET Framework.  
  
 Należy pamiętać, że słowo niższego rzędu w tym adresie zostanie zaokrąglone. Na przykład jeśli określisz 0x11110001, zostanie zaokrąglony do 0x11110000.  
  
 Aby zakończyć proces podpisywania dla dll, należy użyć sn. EXE z opcją -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Kliknij przycisk **Zaawansowane.**  
  
4. Zmodyfikuj właściwość **DLL Base Address.**  
  
     Aby programowo ustawić tę opcję <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>kompilatora, zobacz .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
