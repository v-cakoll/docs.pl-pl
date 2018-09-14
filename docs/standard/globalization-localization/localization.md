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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee7de15130644e63b17a6d067c5cce9088d199a0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521193"
---
# <a name="localization"></a><span data-ttu-id="787a9-102">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="787a9-102">Localization</span></span>
<span data-ttu-id="787a9-103">Lokalizacja jest tłumaczeniem zasobów aplikacji zlokalizowane wersje w każdym kulturę, w której aplikacja będzie obsługiwać proces.</span><span class="sxs-lookup"><span data-stu-id="787a9-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="787a9-104">Należy przejść do kroku lokalizacji, dopiero po ukończeniu [sprawdzenie](../../../docs/standard/globalization-localization/localizability-review.md) krok, aby sprawdzić, czy zglobalizowanej aplikacja jest gotowa do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="787a9-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="787a9-105">Aplikacja, która jest gotowy do lokalizacji jest podzielony dwóch bloków pojęciach, blok, który zawiera wszystkie elementy interfejsu użytkownika i blok, który zawiera kod wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="787a9-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="787a9-106">Blok interfejsu użytkownika zawiera tylko lokalizowalne interfejsu użytkownika elementów, takich jak ciągi, komunikaty o błędach, okna dialogowe, menu, zasoby obiektów osadzonych, i tak dalej dla kultury neutralnej.</span><span class="sxs-lookup"><span data-stu-id="787a9-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="787a9-107">Blok kodu zawiera kod w aplikacji do użycia przez wszystkie obsługiwanych kultur.</span><span class="sxs-lookup"><span data-stu-id="787a9-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="787a9-108">Środowisko uruchomieniowe języka wspólnego obsługuje model zasobów zestawu satelickiego, która oddziela kod wykonywalny aplikacji z jej zasobami.</span><span class="sxs-lookup"><span data-stu-id="787a9-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="787a9-109">Aby uzyskać więcej informacji dotyczących implementowania tego modelu, zobacz [zasoby w aplikacjach pulpitu](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="787a9-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="787a9-110">Dla każdej zlokalizowanej wersji aplikacji należy dodać nowego zestawu satelickiego, który zawiera blok interfejsu użytkownika zlokalizowany przetłumaczyć odpowiedni język dla kultury docelowej.</span><span class="sxs-lookup"><span data-stu-id="787a9-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="787a9-111">Blok kodu dla wszystkich języków pozostają takie same.</span><span class="sxs-lookup"><span data-stu-id="787a9-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="787a9-112">Kombinacja zlokalizowaną wersję bloku interfejsu użytkownika za pomocą bloku kodu tworzy zlokalizowanej wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="787a9-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="787a9-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Dostarcza Edytor zasobów formularzy Windows (Winres.exe), który pozwala na szybkie lokalizowanie formularzy Windows dla kultury docelowej.</span><span class="sxs-lookup"><span data-stu-id="787a9-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="787a9-114">Aby dowiedzieć się, jak za pomocą tego narzędzia, zobacz [Winres.exe (Edytor zasobów Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="787a9-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="787a9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="787a9-115">See also</span></span>

- [<span data-ttu-id="787a9-116">Globalizacja i lokalizacja</span><span class="sxs-lookup"><span data-stu-id="787a9-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
- [<span data-ttu-id="787a9-117">Sprawdzenie możliwości lokalizacji</span><span class="sxs-lookup"><span data-stu-id="787a9-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
- [<span data-ttu-id="787a9-118">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="787a9-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
- [<span data-ttu-id="787a9-119">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="787a9-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
