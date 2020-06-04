---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 99f2b9d65f3c2a128e026666c5efb384e22643f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403151"
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
 Kompilator przetwarza `-moduleassemblyname` opcję tylko wtedy, gdy została `-target:module` określona opcja. Powoduje to, że kompilator tworzy moduł. Moduł utworzony przez kompilator jest prawidłowy tylko dla zestawu określonego przy użyciu `-moduleassemblyname` opcji. Jeśli umieścisz moduł w innym zestawie, wystąpią błędy w czasie wykonywania.  
  
 Ta `-moduleassemblyname` opcja jest wymagana tylko wtedy, gdy są spełnione następujące warunki:  
  
- Typ danych w module wymaga dostępu do `Friend` typu w przywoływanym zestawie.  
  
- Przywoływany zestaw ma udzielony dostęp do zestawu, do którego zostanie skompilowany moduł.  
  
 Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [-Target (Visual Basic)](target.md). Aby uzyskać więcej informacji na temat znajomych zestawów, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> `-moduleassemblyname`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: kompilowanie zestawu wieloplikowego](../../../framework/app-domains/build-multifile-assembly.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-Target (Visual Basic)](target.md)
- [-main](main.md)
- [-Reference (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [Zaprzyjaźnione zestawy](../../../standard/assembly/friend.md)
