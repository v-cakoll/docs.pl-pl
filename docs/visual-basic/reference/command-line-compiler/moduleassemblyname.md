---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a612a68cffd927f3e360406cca6d9daae4f66c86
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775633"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Określa nazwę zestawu, którego częścią ma być ten moduł.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`assembly_name`|Nazwa zestawu, którego częścią ma być ten moduł.|  
  
## <a name="remarks"></a>Uwagi  
 Kompilator przetwarza `-moduleassemblyname` opcję tylko wtedy, `-target:module` gdy została określona opcja. Powoduje to, że kompilator tworzy moduł. Moduł utworzony przez kompilator jest prawidłowy tylko dla zestawu określonego przy użyciu `-moduleassemblyname` opcji. Jeśli umieścisz moduł w innym zestawie, wystąpią błędy w czasie wykonywania.  
  
 Ta `-moduleassemblyname` opcja jest wymagana tylko wtedy, gdy są spełnione następujące warunki:  
  
- Typ danych w module wymaga dostępu do `Friend` typu w przywoływanym zestawie.  
  
- Przywoływany zestaw ma udzielony dostęp do zestawu, do którego zostanie skompilowany moduł.  
  
 Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Aby uzyskać więcej informacji na temat znajomych zestawów, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> `-moduleassemblyname` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: kompilowanie zestawu wieloplikowego](../../../framework/app-domains/build-multifile-assembly.md)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Zaprzyjaźnione zestawy](../../../standard/assembly/friend.md)
