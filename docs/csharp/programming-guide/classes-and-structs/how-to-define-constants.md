---
title: 'Porada: definiowanie stałych w języku C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 15526655de8af6fed464376db1ac761468215210
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337660"
---
# <a name="how-to-define-constants-in-c"></a>Jak zdefiniować stałe w C\#
Stałe są pola, których wartości są ustawiane w czasie kompilacji i nigdy nie można zmienić. Użyj stałych, aby podać znaczące nazwy zamiast literałów liczbowych ("magiczne liczby") dla specjalnych wartości.  
  
> [!NOTE]
> W języku C# [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora nie można używać do definiowania stałych w sposób, który jest zwykle używany w Języku C i C++.  
  
 Aby zdefiniować stałe wartości`int`typów `byte`całkowitych ( , i tak dalej) należy użyć wyliczonego typu. Aby uzyskać więcej informacji, zobacz [wyliczenie](../../language-reference/builtin-types/enum.md).  
  
 Aby zdefiniować stałe nieintegralne, jednym z podejść jest `Constants`grupowanie ich w jednej klasie statycznej o nazwie . Będzie to wymagało, aby wszystkie odwołania do stałych były poprzedzone nazwą klasy, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 Użycie kwalifikatora nazwy klasy pomaga upewnić się, że ty i inni, którzy używają stałej zrozumieć, że jest stała i nie można modyfikować.  
  
## <a name="see-also"></a>Zobacz też

- [Klasy i struktury](./index.md)
