---
title: Niejawnie wpisane wyrażenia lambda
description: Dowiedz się, dlaczego nie można użyć deklaracji zmiennej o typie określonym niejawnie do zadeklarowania wyrażenia lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: c6b0f2666a5c67ce8c89222da5959304ecb8fb93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039130"
---
# <a name="implicitly-typed-lambda-expressions"></a>Niejawnie wpisane wyrażenia lambda

Nie można użyć deklaracji zmiennej typu niejawnie wpisanej do deklarowania wyrażenia lambda.
Tworzy cykliczny problem logiki kompilatora. Deklaracja `var` informuje kompilator, aby ustalić typ zmiennej z typu wyrażenia po prawej stronie operatora przypisania. Wyrażenie lambda nie ma typu czasu kompilacji, ale jest konwertowane na dowolny pasujący delegat lub typ wyrażenia. Po przypisaniu wyrażenia lambda do zmiennej obiektu delegowanego lub typu wyrażenia poinformujesz kompilator, aby wypróbować i skonwertować wyrażenie lambda do wyrażenia lub delegata, który pasuje do sygnatury zmiennej "Assigned to". Kompilator musi próbować wykonać tę czynność po prawej stronie przypisania dopasowuje się do typu po lewej stronie przypisania. 

Obie strony przypisania nie mogą być informować kompilatora, aby wyszukać obiekt po drugiej stronie operatora przypisania i zobaczyć, czy mój typ jest zgodny.

Możesz uzyskać jeszcze więcej szczegółowych informacji na temat tego C# , dlaczego język określa takie zachowanie, czytając [ten artykuł](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (pobieranie plików PDF)
