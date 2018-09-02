---
title: 'Podstawowe wiadomości: Obsługa hosta sieci Web'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 8ee107ffcb9fab629541ce004d1c587fcad652c8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385971"
---
# <a name="core-communications-webhost-support"></a>Podstawowe wiadomości: Obsługa hosta sieci Web

Ten temat zawiera listę wszystkich wyjątków generowanych przez Obsługa.

## <a name="exception-list"></a>Lista wyjątków

|Kod zasobu|Ciąg zasobu|
|-------------------|---------------------|
|Hosting_CompatibilityServiceNotHosted|Ta usługa wymaga zgodności z platformą ASP.NET. Musi on również obsługiwane w usługach IIS. Albo hosta usłudze zgodność platformy ASP.NET w usługach IIS włączone w pliku Web.config, lub ustaw właściwość AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirements do wartości innej niż wymagane.|
|Hosting_ListenerNotFoundForActivationInRecycling|Aktywnie nasłuchuje żaden kanał pod podanym adresem. Jeśli aplikacja jest odtwarzane, usługa jest zamknięty.|
|Hosting_NonHTTPInCompatibilityMode|Tylko protokoły, które są objęte zgodność platformy ASP.NET to HTTP i HTTPS. Usuń wskazany punkt końcowy lub wyłącz zgodność platformy ASP.NET dla aplikacji.|
|Hosting_ProcessNotExecutingUnderHostedContext|Nie można wywołać określonego procesu hostingu w bieżącym środowisku macierzystym. Ten interfejs API wymaga, że aplikacja wywołująca jest hostowane w Internet Information Services lub usługi Windows Process Activation Service.|
|Hosting_ServiceCompatibilityRequire|Nie można aktywować usługi, ponieważ wymaga ona zgodność platformy ASP.NET. Zgodność platformy ASP.NET nie jest włączona dla tej aplikacji. Włącz zgodność platformy ASP.NET w pliku Web.config albo ustaw AspNetCompatibilityRequirementsAttribute.AspNetCompatibility.|
