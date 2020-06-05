---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 34dbf36cc79a8c4715cf6a07c57d559e14f40030
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363633"
---
# <a name="-codepage-visual-basic"></a>-CodePage (Visual Basic)
Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`id`|Wymagany. Kompilator używa strony kodowej określonej przez program, `id` Aby interpretować Kodowanie plików źródłowych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby skompilować kod źródłowy zapisany z określonym kodowaniem, możesz użyć, `-codepage` Aby określić, która strona kodowa powinna być używana. `-codepage`Opcja ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [kodowanie znaków w .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 `-codepage`Opcja nie jest wymagana, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 z podpisem. Program Visual Studio zapisuje wszystkie pliki kodu źródłowego z bieżącą stroną kodową ANSI domyślnie, chyba że użytkownik określi inne kodowanie w oknie dialogowym **kodowanie** . Program Visual Studio używa okna dialogowego **kodowanie** do otwierania plików kodu źródłowego zapisanych z inną stroną kodową.  
  
> [!NOTE]
> `-codepage`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
