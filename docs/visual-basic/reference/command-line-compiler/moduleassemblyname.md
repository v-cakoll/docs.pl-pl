---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 5b26e36346858d95526f5d5ce7d4645bea1dbe05
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005479"
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
 Kompilator przetwarza opcję `-moduleassemblyname` tylko wtedy, gdy została określona opcja `-target:module`. Powoduje to, że kompilator tworzy moduł. Moduł utworzony przez kompilator jest prawidłowy tylko dla zestawu określonego przy użyciu opcji `-moduleassemblyname`. Jeśli umieścisz moduł w innym zestawie, wystąpią błędy w czasie wykonywania.  
  
 Opcja `-moduleassemblyname` jest wymagana tylko wtedy, gdy są spełnione następujące warunki:  
  
- Typ danych w module wymaga dostępu do typu `Friend` w przywoływanym zestawie.  
  
- Przywoływany zestaw ma udzielony dostęp do zestawu, do którego zostanie skompilowany moduł.  
  
 Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Aby uzyskać więcej informacji na temat znajomych zestawów, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> Opcja `-moduleassemblyname` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: kompilacja zestawów wieloplikowych](../../../framework/app-domains/build-multifile-assembly.md)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Przyjazne zestawy](../../../standard/assembly/friend.md)
