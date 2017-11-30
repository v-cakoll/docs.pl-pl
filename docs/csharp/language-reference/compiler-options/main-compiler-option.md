---
title: -main (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6dca6e62dbf69783babf2e16dc4e7c36c6705c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="main-c-compiler-options"></a>/main (opcje kompilatora C#)
Ta opcja określa klasę, która zawiera wpis wskaż program, jeśli zawiera więcej niż jedną klasę **Main** metody.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a>Argumenty  
 `class`  
 Typ zawierający **Main** metody.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli Twoje kompilacji zawiera więcej niż jeden typ z [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody, można określić, którego typ zawiera **Main** metodę, która ma być używany jako punkt wejścia do programu.  
  
 Ta opcja jest przeznaczona do użytku podczas kompilowania pliku .exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **obiekt uruchomieniowy** właściwości.  
  
     Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t2.cs` i `t3.cs`, określania który **Main** będzie można znaleźć metody w `Test2`:  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
