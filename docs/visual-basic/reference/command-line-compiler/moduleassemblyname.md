---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a16dd616c8a38dea4bd1779e4feea779b3a18e2d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375301"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Określa nazwę zestawu, który będzie należeć tego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`assembly_name`|Nazwa zestawu, który będzie należeć tego modułu.|  
  
## <a name="remarks"></a>Uwagi  
 Procesy kompilatora `-moduleassemblyname` tylko wtedy, gdy opcja `-target:module` określono opcję. Powoduje to, że kompilator Utwórz moduł. Moduł, który został utworzony przez kompilator jest prawidłowy tylko w przypadku zestawu określony za pomocą `-moduleassemblyname` opcji. Jeśli umieścisz modułu w innym zestawie będzie pojawiają się błędy czasu wykonywania.  
  
 `-moduleassemblyname` Opcja jest potrzebna tylko wtedy, gdy spełnione są poniższe warunki:  
  
-   Typ danych w module musi mieć dostęp do `Friend` typu w zestawie odwołania.  
  
-   Przywoływany zestaw przyznał prawa dostępu do zestawu friend do zestawu, do którego zostanie skompilowany moduł.  
  
 Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Aby uzyskać więcej informacji na temat przyjaznych zestawów, zobacz [przyjaznych zestawów](../../../standard/assembly/friend-assemblies.md).  
  
> [!NOTE]
>  `-moduleassemblyname` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilacji z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Kompilacja zestawów wieloplikowych](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [— Odwołanie (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Przyjazne zestawy](../../../standard/assembly/friend-assemblies.md)
