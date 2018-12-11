---
title: goto — instrukcja - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: bfc997631cc147bf5718ec91a57e2995cead052f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236768"
---
# <a name="goto-c-reference"></a>goto (odwołanie w C#)

`goto` Instrukcja przekazuje kontrolę nad programem bezpośrednio do instrukcji oznaczonej etykietą.

Typowym zastosowaniem `goto` jest kontrola jest przekazywana do określoną etykietą przypadku switch lub etykieta domyślna w `switch` instrukcji.

`goto` Instrukcji warto wykorzystać pętli głęboko zagnieżdżonych.

## <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie `goto` w [Przełącz](switch.md) instrukcji.

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie `goto` umożliwiające rozbicie z zagnieżdżonej pętli.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [goto, instrukcja (C++)](/cpp/cpp/goto-statement-cpp)  
- [Instrukcje skoku](jump-statements.md)  
