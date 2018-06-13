---
title: Podstawowe operacje na ciągach w programie .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7692251a00c712f93b649d4cd6fc153bb248f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567487"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="7a3d6-102">Podstawowe operacje na ciągach w .NET</span><span class="sxs-lookup"><span data-stu-id="7a3d6-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="7a3d6-103">Aplikacje często odpowiadają użytkownikom tworząc wiadomości w oparciu o dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="7a3d6-104">Na przykład nie jest nietypowe dla witryn sieci Web odpowiadanie na nowo zalogowanego użytkownika o specjalne powitanie zawierające nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="7a3d6-105">Kilka metod w <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy umożliwiają dynamicznie utworzyć niestandardowe ciągi do wyświetlenia w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="7a3d6-106">Te metody także pomóc wykonywać podstawowe operacje na ciągach, takich jak tworzenie nowych ciągów w tablice bajtów, porównanie wartości ciągów i modyfikowanie istniejących ciągów.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a3d6-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7a3d6-107">In This Section</span></span>  
 [<span data-ttu-id="7a3d6-108">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="7a3d6-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="7a3d6-109">Opisuje podstawowe sposoby Konwertowanie obiektów do ciągów i łączenie ciągów.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="7a3d6-110">Przycinanie i usuwanie znaków</span><span class="sxs-lookup"><span data-stu-id="7a3d6-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="7a3d6-111">Opisuje sposób przycięcia lub usuń znaki w ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="7a3d6-112">Uzupełnianie ciągów</span><span class="sxs-lookup"><span data-stu-id="7a3d6-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="7a3d6-113">Opisuje sposób wstawiania znaków lub pustych miejsc w ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="7a3d6-114">Porównywanie ciągów</span><span class="sxs-lookup"><span data-stu-id="7a3d6-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="7a3d6-115">Opisuje sposób porównywanie zawartości dwóch lub więcej ciągów.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="7a3d6-116">Zmienianie wielkości liter</span><span class="sxs-lookup"><span data-stu-id="7a3d6-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="7a3d6-117">Zawiera opis sposobu zmiany w przypadku znaków ciągu.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="7a3d6-118">Używanie klasy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="7a3d6-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="7a3d6-119">Opisuje sposób tworzenia i modyfikowania obiektów ciąg dynamiczny <xref:System.Text.StringBuilder> klasy.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="7a3d6-120">Instrukcje: Wykonywanie podstawowych działań na ciągach</span><span class="sxs-lookup"><span data-stu-id="7a3d6-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="7a3d6-121">Pokazuje użycie podstawowe operacje na ciągach.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7a3d6-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7a3d6-122">Related Sections</span></span>  
 [<span data-ttu-id="7a3d6-123">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="7a3d6-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="7a3d6-124">Opisuje sposób konwertowania jednego typu do innego typu.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="7a3d6-125">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="7a3d6-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="7a3d6-126">Opisuje sposób formatowania ciągów za pomocą specyfikatory formatu.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-126">Describes how to format strings using format specifiers.</span></span>
