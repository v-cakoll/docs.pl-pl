---
title: Lokalizacja
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 89851c42570f301bee8a3eca744eb5d069347d4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120875"
---
# <a name="localization"></a><span data-ttu-id="c2efe-102">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="c2efe-102">Localization</span></span>

<span data-ttu-id="c2efe-103">Lokalizacja jest procesem tłumaczenia zasobów aplikacji na zlokalizowane wersje dla każdej kultury, która będzie obsługiwana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c2efe-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="c2efe-104">Należy przejść do kroku lokalizacji tylko po zakończeniu kroku [Przegląd lokalizacji,](../../../docs/standard/globalization-localization/localizability-review.md) aby sprawdzić, czy zglobalizowana aplikacja jest gotowa do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c2efe-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="c2efe-105">Aplikacja, która jest gotowa do lokalizacji jest podzielona na dwa bloki koncepcyjne: blok, który zawiera wszystkie elementy interfejsu użytkownika i blok, który zawiera kod wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="c2efe-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="c2efe-106">Blok interfejsu użytkownika zawiera tylko zlokalizowane elementy interfejsu użytkownika, takie jak ciągi, komunikaty o błędach, okna dialogowe, menu, zasoby obiektów osadzonych i tak dalej dla kultury neutralnej.</span><span class="sxs-lookup"><span data-stu-id="c2efe-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="c2efe-107">Blok kodu zawiera tylko kod aplikacji, który ma być używany przez wszystkie obsługiwane kultury.</span><span class="sxs-lookup"><span data-stu-id="c2efe-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="c2efe-108">Czas wykonywania języka wspólnego obsługuje model zasobów zestawu satelitarnego, który oddziela kod wykonywalny aplikacji z jego zasobów.</span><span class="sxs-lookup"><span data-stu-id="c2efe-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="c2efe-109">Aby uzyskać więcej informacji na temat implementowania tego modelu, zobacz [Zasoby w .NET](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="c2efe-109">For more information about implementing this model, see [Resources in .NET](../../../docs/framework/resources/index.md).</span></span>

<span data-ttu-id="c2efe-110">Dla każdej zlokalizowanej wersji aplikacji dodaj nowy zestaw satelicki, który zawiera zlokalizowany blok interfejsu użytkownika przetłumaczony na odpowiedni język dla kultury docelowej.</span><span class="sxs-lookup"><span data-stu-id="c2efe-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="c2efe-111">Blok kodu dla wszystkich kultur powinny pozostać takie same.</span><span class="sxs-lookup"><span data-stu-id="c2efe-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="c2efe-112">Połączenie zlokalizowanej wersji bloku interfejsu użytkownika z blokiem kodu tworzy zlokalizowaną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2efe-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="c2efe-113">Zestaw Windows Software Development Kit (SDK) dostarcza Edytor zasobów formularzy systemu Windows (Winres.exe), który umożliwia szybkie lokalizowanie formularzy systemu Windows dla kultur docelowych.</span><span class="sxs-lookup"><span data-stu-id="c2efe-113">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="c2efe-114">Aby uzyskać informacje dotyczące korzystania z tego narzędzia, zobacz [Winres.exe (Edytor zasobów formularzy systemu Windows)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="c2efe-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2efe-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2efe-115">See also</span></span>

- [<span data-ttu-id="c2efe-116">Globalizacja i lokalizacja</span><span class="sxs-lookup"><span data-stu-id="c2efe-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="c2efe-117">Localizability Recenzja</span><span class="sxs-lookup"><span data-stu-id="c2efe-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)
- [<span data-ttu-id="c2efe-118">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="c2efe-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="c2efe-119">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="c2efe-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
