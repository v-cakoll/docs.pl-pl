---
title: Podstawowe operacje ciągu w .NET
description: Dowiedz się więcej o podstawowych operacjach, które można wykonywać na ciągach.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 2ce1b148a2b1605b5b1283bdc3398409661f3f83
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523988"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="24845-103">Podstawowe operacje ciągu w .NET</span><span class="sxs-lookup"><span data-stu-id="24845-103">Basic string operations in .NET</span></span>

<span data-ttu-id="24845-104">Aplikacje często reagują na użytkowników, konstruując wiadomości na podstawie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24845-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="24845-105">Na przykład nie jest rzadkością dla witryn sieci Web, aby odpowiedzieć na nowo zalogowanego użytkownika z specjalistycznym powitaniem, który zawiera nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24845-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="24845-106">Kilka metod <xref:System.String?displayProperty=nameWithType> w <xref:System.Text.StringBuilder?displayProperty=nameWithType> i klasy umożliwiają dynamicznie konstruowania ciągów niestandardowych do wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24845-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="24845-107">Metody te pomagają również wykonywać szereg podstawowych operacji ciągu, takich jak tworzenie nowych ciągów z tablic bajtów, porównywanie wartości ciągów i modyfikowanie istniejących ciągów.</span><span class="sxs-lookup"><span data-stu-id="24845-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="24845-108">Powiązane sekcje</span><span class="sxs-lookup"><span data-stu-id="24845-108">Related sections</span></span>

<span data-ttu-id="24845-109">[Wpisz konwersję w .NET](../../../docs/standard/base-types/type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="24845-109">[Type Conversion in .NET](../../../docs/standard/base-types/type-conversion.md)</span></span>\
<span data-ttu-id="24845-110">W tym artykule opisano sposób konwertowania jednego typu na inny typ.</span><span class="sxs-lookup"><span data-stu-id="24845-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="24845-111">[Typy formatowania](../../../docs/standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="24845-111">[Formatting Types](../../../docs/standard/base-types/formatting-types.md)</span></span>\
<span data-ttu-id="24845-112">W tym artykule opisano sposób formatowania ciągów przy użyciu specyfikatorów formatu.</span><span class="sxs-lookup"><span data-stu-id="24845-112">Describes how to format strings using format specifiers.</span></span>
