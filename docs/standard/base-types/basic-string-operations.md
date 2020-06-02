---
title: Podstawowe operacje na ciągach w programie .NET
description: Zapoznaj się z podstawowymi operacjami, które można wykonywać na ciągach.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 8c19f6bcbdf5e4829c91aee1e2fd631537ed2e0a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277755"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="5d921-103">Podstawowe operacje na ciągach w programie .NET</span><span class="sxs-lookup"><span data-stu-id="5d921-103">Basic string operations in .NET</span></span>

<span data-ttu-id="5d921-104">Aplikacje często odpowiadają użytkownikom przez konstruowanie komunikatów na podstawie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d921-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="5d921-105">Na przykład nie jest to zdarza się, aby witryny sieci Web odpowiadały nowo zalogowanemu użytkownikowi z wyspecjalizowanym powitaniem zawierającym nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d921-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="5d921-106">Kilka metod w <xref:System.String?displayProperty=nameWithType> <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasach i pozwala na dynamiczne konstruowanie ciągów niestandardowych do wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d921-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="5d921-107">Te metody ułatwiają również wykonywanie wielu podstawowych operacji na ciągach, takich jak tworzenie nowych ciągów z tablic bajtów, porównywanie wartości ciągów i modyfikowanie istniejących ciągów.</span><span class="sxs-lookup"><span data-stu-id="5d921-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="5d921-108">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5d921-108">Related sections</span></span>

<span data-ttu-id="5d921-109">[Konwersja typów w programie .NET](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="5d921-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="5d921-110">Opisuje sposób konwersji jednego typu na inny typ.</span><span class="sxs-lookup"><span data-stu-id="5d921-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="5d921-111">[Formatowanie typów](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="5d921-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="5d921-112">Opisuje sposób formatowania ciągów przy użyciu specyfikatorów formatu.</span><span class="sxs-lookup"><span data-stu-id="5d921-112">Describes how to format strings using format specifiers.</span></span>
