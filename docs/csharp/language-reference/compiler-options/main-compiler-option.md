---
title: -main (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602727"
---
# <a name="-main-c-compiler-options"></a>-main (opcje kompilatora C#)
Ta opcja określa klasę, która zawiera punkt wejścia do programu, jeśli więcej niż jedna klasa zawiera **Main** metody.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Argumenty  
 `class`  
 Typ, który zawiera **Main** metody.  
 Podana nazwa klasy musi być w pełni kwalifikowana; musi zawierać pełną przestrzeń nazw zawierającą klasę, a następnie nazwę klasy. Na przykład gdy `Main` metoda znajduje `Program` się wewnątrz `MyApplication.Core` klasy w przestrzeni nazw, `-main:MyApplication.Core.Program`opcja kompilatora musi być .
  
## <a name="remarks"></a>Uwagi  
 Jeśli kompilacja zawiera więcej niż jeden typ z [Main](../../programming-guide/main-and-command-args/index.md) metody, można określić, który typ zawiera **Main** metoda, która ma być używana jako punkt wejścia do programu.  
  
 Ta opcja jest używana podczas kompilowania pliku exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **właściwości Application.**  
  
3. Zmodyfikuj właściwość **Startup object.**  
  
     Aby programowo ustawić tę opcję <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Skompiluj `t2.cs` i `t3.cs`, określając, że metoda **główna** zostanie znaleziona w `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
