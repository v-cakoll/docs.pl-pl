---
title: Wyrażenia lambda wpisane niejawnie
description: Dowiedz się, dlaczego nie można użyć deklaracji zmiennej niejawnie wpisane do deklarowania wyrażenia lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145725"
---
# <a name="implicitly-typed-lambda-expressions"></a>Wyrażenia lambda wpisane niejawnie

Nie można użyć niejawnie wpisane deklaracji zmiennej do deklarowania wyrażenia lambda.
Tworzy problem logiki cyklicznej dla kompilatora. Deklaracja `var` informuje kompilator, aby dowiedzieć się typ zmiennej z typu wyrażenia po prawej stronie operatora przypisania. Wyrażenie lambda nie ma typu czasu kompilacji, ale jest konwertowalne do dowolnego pasującego delegata lub typu wyrażenia. Po przypisaniu wyrażenia lambda do zmiennej typu delegata lub wyrażenia, należy powiedzieć kompilatorowi, aby spróbować przekonwertować wyrażenie lambda do wyrażenia lub delegata, który pasuje do podpisu zmiennej "przypisane do". Kompilator musi starać się, aby rzecz po prawej stronie przypisania była zgodna z typem po lewej stronie przypisania.

Obie strony przypisania nie można poinformować kompilatora, aby spojrzeć na obiekt po drugiej stronie operatora przypisania i sprawdzić, czy mój typ pasuje.

Możesz uzyskać jeszcze więcej szczegółów na temat tego, dlaczego język Języka C# określa to zachowanie, czytając [ten artykuł](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (plik PDF do pobrania).
