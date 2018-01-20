---
title: -nostdlib (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dd9d2b6a4a9c774aa339e840ad0020ee39cb10d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (opcje kompilatora C#)
**-nostdlib** uniemożliwia importowanie pliku mscorlib.dll, która określa całą przestrzeń nazw systemu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, jeśli chcesz zdefiniować lub utworzyć własne systemową przestrzenią nazw i obiektów.  
  
 Jeśli nie określisz **- nostdlib**, mscorlib.dll zostaną zaimportowane do programu (jak w przypadku określania **- nostdlib-**). Określanie **- nostdlib** jest taka sama jak określanie **- nostdlib +**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz **właściwości** strony dla projektu.  
  
2.  Kliknij przycisk **kompilacji** stronę właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **nie odwołuj się do pliku mscorlib.dll** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
