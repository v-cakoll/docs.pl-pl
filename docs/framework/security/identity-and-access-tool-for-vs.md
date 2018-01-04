---
title: "Tożsamość i narzędzie dostępu do programu Visual Studio 2012"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 079c3798f17f4929124cd5cb027baa5d40a1167a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Tożsamość i narzędzie dostępu do programu Visual Studio 2012
W tym temacie opisano nowe narzędzie tożsamości i dostępu dla programu Visual Studio 11. To narzędzie można pobrać z następującego adresu URL: [http://go.microsoft.com/fwlink/?LinkID=245849](http://go.microsoft.com/fwlink/?LinkID=245849) lub bezpośrednio w programie Visual Studio 11, wyszukując "identity" bezpośrednio w Menedżerze rozszerzeń.  
  
 Narzędzie tożsamości i dostępu dla programu Visual Studio 11 znacznie upraszcza projektowanie aplikacji dzięki następującym głównym funkcjom:  
  
-   Za pomocą tego nowego narzędzia możesz tworzyć aplikacje przy użyciu typów projektów aplikacji sieci Web i szybko integrować je z programem IIS.  
  
-   W odróżnieniu od uwierzytelniania mającego zapewnić samą ochronę, za pomocą tego nowego narzędzia możesz określić stronę wykrywania/kontroler w lokalnym obszarze głównym (lub dowolny inny punkt końcowy obsługujący uwierzytelnianie w aplikacji), a program WIF skonfiguruje wszystkie nieuwierzytelnione żądania do docierania tam zamiast przekierowywać je do usługi STS.  
  
-   To narzędzie zawiera usługę tokenu zabezpieczającego (STS), która jest uruchamiana na komputerze lokalnym z chwilą rozpoczęcia sesji debugowania. W związku z tym nie musisz już tworzyć niestandardowych projektów usługi STS i dostosowywać ich w celu uzyskania oświadczeń potrzebnych do testowania aplikacji. Typy i wartości oświadczeń są w pełni konfigurowalne.  
  
-   Typowe ustawienia możesz modyfikować bezpośrednio za pośrednictwem interfejsu użytkownika tego narzędzia, bez konieczności modyfikowania pliku web.config.  
  
-   Za pomocą jednego ekranu możesz ustanowić federację z usługą Active Directory Federation Services (AD FS) 2.0 (lub innymi dostawcami protokołu WS-Federation).  
  
-   Narzędzie wykorzystuje możliwości usługi kontroli dostępu (ACS) systemu Microsoft Azure, wyświetlając prostą listę pól wyboru odpowiadających wszystkim dostawcom tożsamości, których chcesz używać: Facebook, Google, Live ID, Yahoo!, dowolny dostawca protokołu OpenID i dowolny dostawca protokołu WS-Federation. Wybierz swoich dostawców tożsamości, kliknij przycisk OK, a następnie naciśnij klawisz F5, i aplikacja i usługa ACS zostaną automatycznie skonfigurowane, a aplikacja testowa będzie obsługiwać usługę ACS.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje programu WIF](../../../docs/framework/security/wif-features.md)
