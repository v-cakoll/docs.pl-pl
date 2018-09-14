---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: fda75383435fdff718d1d50bc8583afc9858e7e2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515487"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Określa stronę kodową dla wszystkich plików kodu źródłowego w kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`id`|Wymagane. Kompilator używa strony kodowej, określony przez `id` interpretowanie kodowanie plików źródłowych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `-codepage` można określić stronę kodową, która będzie używana. `-codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [kodowanie znaków na platformie .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 `-codepage` Opcja nie jest potrzebna, jeśli zostały zapisane pliki kodu źródłowego, przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 z podpisem. Program Visual Studio zapisuje wszystkie pliki kodu źródłowego za pomocą bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi, inne kodowanie w **kodowanie** okno dialogowe. Program Visual Studio używa **kodowanie** okno dialogowe Otwieranie plików kodu źródłowego, zapisany z inną stronę kodową.  
  
> [!NOTE]
>  `-codepage` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
