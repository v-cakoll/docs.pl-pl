---
title: -BaseAddress (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937211"
---
# <a name="-baseaddress-c-compiler-options"></a>-BaseAddress (C# opcje kompilatora)
Opcja **-BaseAddress** pozwala określić preferowany adres podstawowy, przy użyciu którego ma zostać ZAŁADOWANA Biblioteka DLL. Aby uzyskać więcej informacji na temat tego, kiedy i dlaczego należy używać tej opcji, zobacz [dziennik sieci Web Larry Osterman](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Adres podstawowy biblioteki DLL. Ten adres można określić jako liczbę dziesiętną, szesnastkową lub ósemkową.  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego .NET Framework.  
  
 Należy pamiętać, że Dolna kolejność wyrazów w tym adresie zostanie zaokrąglona. Na przykład, jeśli określisz 0x11110001, zostanie ona zaokrąglona do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, Użyj SN. EXE z opcją-R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Kliknij przycisk **Zaawansowane** .  
  
4. Zmodyfikuj właściwość **adresu podstawowego biblioteki DLL** .  
  
     Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
