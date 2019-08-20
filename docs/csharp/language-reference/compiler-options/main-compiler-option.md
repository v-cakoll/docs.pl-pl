---
title: -Main (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602727"
---
# <a name="-main-c-compiler-options"></a>-Main (C# opcje kompilatora)
Ta opcja określa klasę, która zawiera punkt wejścia do programu, jeśli więcej niż jedna Klasa zawiera metodę **Main** .  
  
## <a name="syntax"></a>Składnia  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Argumenty  
 `class`  
 Typ, który zawiera metodę **Main** .  
 Podana nazwa klasy musi być w pełni kwalifikowana; musi zawierać pełną przestrzeń nazw zawierającą klasę, a po niej nazwę klasy. `Main` Na przykład, gdy metoda znajduje się `Program` wewnątrz klasy w `MyApplication.Core` przestrzeni nazw, opcja kompilatora musi mieć `-main:MyApplication.Core.Program`wartość.
  
## <a name="remarks"></a>Uwagi  
 Jeśli kompilacja zawiera więcej niż jeden typ z metodą [Main](../../programming-guide/main-and-command-args/index.md) , można określić, który typ zawiera metodę **Main** , która ma być używana jako punkt wejścia do programu.  
  
 Ta opcja jest używana podczas kompilowania pliku. exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **aplikacji** .  
  
3. Zmodyfikuj właściwość **obiektu uruchomieniowego** .  
  
     Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t2.cs` `Test2`i `t3.cs`, określając, że metoda **Main** zostanie znaleziona w:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
