---
title: "Kod o przezroczystym poziomie bezpieczeństwa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 996da59640281c8584774fa9e66b42619753afb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="security-transparent-code"></a>Kod o przezroczystym poziomie bezpieczeństwa
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Zabezpieczeń obejmuje trzy wchodzącymi w interakcje: sandboxing, uprawnienia i wymuszania. Sandboxing odwołuje się do rozwiązań tworzenia izolowanego domen, gdy kod jest traktowana jako kod w pełni zaufanych i innych jest ograniczony do uprawnień w zestaw piaskownicy uprawnień. Kod aplikacji, który jest uruchamiany w ramach zestawu grant piaskownicy jest traktowany jako przezroczysty; oznacza to, że nie może wykonywać wszystkie operacje, które mogą mieć wpływ na bezpieczeństwo. Zestaw do piaskownicy jest określany przez dowód uprawnień (<xref:System.Security.Policy.Evidence> klasy). Dowód identyfikuje określone uprawnienia są wymagane przez piaskownic i mogą być tworzone jakiego rodzaju obszarów izolowanych. Wymuszanie odwołuje się stosowanie kod o przezroczystym można wykonać tylko w obrębie jej zestaw uprawnień.  
  
> [!IMPORTANT]
>  Zasady zabezpieczeń jest kluczowym elementem w poprzednich wersjach programu .NET Framework. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zasady zabezpieczeń jest przestarzały. Eliminacja zasady zabezpieczeń jest oddzielony od przezroczystość zabezpieczeń. Aby uzyskać informacje o skutkach tej zmiany, zobacz [zgodności zasad zabezpieczeń dostępu kodu i migracji](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).  
  
 W tym temacie opisano szczegółowo w modelu przezroczystości. Ten temat zawiera następujące sekcje:  
  
-   [Cel modelu przezroczystości](#purpose)  
  
-   [Określanie poziom przezroczystości](#level)  
  
-   [Wymuszanie przezroczystości](#enforcement)  
  
<a name="purpose"></a>   
## <a name="purpose-of-the-transparency-model"></a>Cel modelu przezroczystości  
 Przezroczystość jest mechanizm wymuszania, która oddziela kod, który działa jako część aplikacji z kodu, który działa jako część infrastruktury. Przezroczystość rysuje barierę między kod, który można wykonać czynności uprzywilejowanym (kod krytyczne), taką jak wywołanie kodu natywnego i kodu, który nie (kod o przezroczystym). Kod o przezroczystym można wykonywać polecenia w granicach zestaw uprawnień, który działa w, ale nie można wykonać, pochodzi z ani zawierać kodu krytycznego.  
  
 Podstawowym celem wymuszania przezroczystość jest zapewnienie prosty i efektywny mechanizm izolowanie różnych grup kodu opartego na uprawnień. W ramach modelu sandboxing grupy te uprawnienia są całkowicie zaufane (to znaczy nie ograniczona) lub częściowo zaufany (to znaczy ograniczone do uprawnień przyznanych ustawioną piaskownicy).  
  
> [!IMPORTANT]
>  Modelu przezroczystości transcends zabezpieczenia dostępu kodu. Przezroczystość jest wymuszana przez kompilatora just in time i obowiązuje niezależnie od grant zestawu dla zestawu, w tym trybie pełnego zaufania.  
  
 Przezroczystość została wprowadzona w programie .NET Framework w wersji 2.0 uprościć model zabezpieczeń i łatwiejsze do zapisywania i wdrażanie bezpiecznych bibliotek i aplikacji. Kod o przezroczystym służy także w programie Microsoft Silverlight, aby uprościć tworzenie aplikacji częściowo zaufany.  
  
> [!NOTE]
>  Podczas opracowywania aplikacji częściowo zaufanej ma pod uwagę wymagania dotyczące uprawnień dla hostów docelowych. Możesz utworzyć aplikację, która używa zasobów, które nie są dozwolone przez niektóre hosty. Ta aplikacja zostanie skompilowany bez błędów, ale zakończy się niepowodzeniem, gdy jest ładowany w udostępnianym środowisku. Jeśli utworzono aplikację za pomocą programu Visual Studio, można włączyć debugowanie w częściowej relacji zaufania lub zestawu ze środowiska projektowego ograniczonych uprawnień. Aby uzyskać więcej informacji, zobacz [porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). Funkcja obliczania uprawnienia podany dla aplikacji ClickOnce jest również dostępna dla dowolnej aplikacji, częściowo zaufany.  
  
 [Powrót do początku](#top)  
  
<a name="level"></a>   
## <a name="specifying-the-transparency-level"></a>Określanie poziomu przezroczystości  
 Poziom zestawu <xref:System.Security.SecurityRulesAttribute> atrybutu jawnie wybiera <xref:System.Security.SecurityRuleSet> zasady obowiązujące zestawu. Reguły są pogrupowane w ramach liczbowych poziomu systemu, gdzie wyższe poziomy oznacza wymuszania zwiększenie poziomu zasad zabezpieczeń.  
  
 Te poziomy są następujące:  
  
-   Poziom 2 (<xref:System.Security.SecurityRuleSet.Level2>) — [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] reguł przezroczystości.  
  
-   Poziom 1 (<xref:System.Security.SecurityRuleSet.Level1>) — reguł przezroczystości .NET Framework 2.0.  
  
 Podstawowe różnice między poziomami dwóch przezroczystość jest, że poziom 1 nie obsługuje wymuszania reguł przezroczystości dla połączeń z poza zestaw i jest przeznaczona tylko dla zgodności.  
  
> [!IMPORTANT]
>  Należy określić poziom 1 przezroczystość zgodności. oznacza to, określić poziom 1 tylko dla kodu, który został opracowany przy użyciu programu .NET Framework 3.5 lub starszej korzystającego z <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu albo nie używa modelu przezroczystości. Na przykład użyć przezroczystość poziomu 1 dla zestawów platformy .NET Framework 2.0, które zezwala na wywołania z częściowo zaufanych wywołań (APTCA). Kod, który został utworzony dla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], należy zawsze używać przezroczystość poziomu 2.  
  
### <a name="level-2-transparency"></a>Przezroczystość poziomu 2  
 Przezroczystość poziomu 2 została wprowadzona w systemie [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Trzy zasady tego modelu są kod o przezroczystym, bezpieczne-kod krytyczny dla zabezpieczeń i kod krytyczny dla zabezpieczeń.  
  
-   Kod o przezroczystym, niezależnie od uprawnień, które otrzymuje (w tym trybie pełnego zaufania), można wywołać tylko innych kod o przezroczystym lub bezpieczne-kod krytyczny dla zabezpieczeń. Jeśli kod jest częściowo zaufany, może wyłącznie wykonywać akcje, które są dozwolone w zestawie uprawnień w domenie. Kod o przezroczystym nie może wykonać następujące czynności:  
  
    -   Wykonaj <xref:System.Security.CodeAccessPermission.Assert%2A> operacji lub podniesienie uprawnień.  
  
    -   Zawiera kod niezabezpieczony lub niemożliwy.  
  
    -   Bezpośrednio wywoływać kod krytyczny.  
  
    -   Wywołanie kodu natywnego lub kod, który ma <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.  
  
    -   Wywołanie elementu członkowskiego, który jest chroniony przez <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Dziedziczy z typu krytycznego.  
  
     Ponadto jawne metody nie można zastąpić krytycznych metod wirtualnych lub implementować metod interfejsu krytyczne.  
  
-   Safe-kod krytyczny dla zabezpieczeń jest w pełni zaufany, ale jest wywołane przez kod przezroczysty. Prezentuje ona ograniczona powierzchni kodu pełnego zaufania. Weryfikacji prawidłowości i zabezpieczeń się tak zdarzyć w kodzie bezpieczne krytyczne.  
  
-   Kod krytyczny dla zabezpieczeń można wywołać żadnego kodu i jest w pełni zaufany, ale nie można wywołać przez kod przezroczysty.  
  
### <a name="level-1-transparency"></a>Poziom 1 przezroczystości  
 Poziom 1 modelu przezroczystości została wprowadzona w programie .NET Framework w wersji 2.0 umożliwia deweloperom zmniejszyć ilość kodu, który podlega inspekcji zabezpieczeń. Chociaż przezroczystość poziomu 1 był publicznie dostępne w wersji 2.0, przede wszystkim wykorzystano tylko w ramach firmy Microsoft na potrzeby inspekcji zabezpieczeń. Za pomocą adnotacji deweloperzy mogą zadeklarować typy, które mogą wykonać członkowie wybierającym zabezpieczeń i innych zaufanych akcji (krytyczny dla zabezpieczeń) i nie może (przezroczystym poziomie bezpieczeństwa). Kod, który jest identyfikowany jako przezroczysty nie wymaga wysoki stopień inspekcji zabezpieczeń. Przezroczystość poziomu 1 stwierdza, że wymuszania przezroczystość jest ograniczona do w zestawie. Innymi słowy ani typy publiczne elementy członkowskie, które zostały zidentyfikowane jako krytyczny dla zabezpieczeń są krytyczny dla zabezpieczeń tylko w zestawie. Jeśli użytkownik chce wymusić zabezpieczeń dla tych typów i członków, gdy są one nazywane z poza zestaw, należy użyć linkdemand dla pełnego zaufania. Jeśli nie chcesz, widocznego publicznie krytyczny dla zabezpieczeń typy i składniki są traktowane jako bezpieczny krytyczny dla zabezpieczeń i może być wywoływany przez kod częściowo zaufany poza zestaw.  
  
 Model przezroczystość poziomu 1 ma następujące ograniczenia:  
  
-   Typy krytyczny dla zabezpieczeń i elementów członkowskich, które są publiczne są dostępne z kod o przezroczystym poziomie bezpieczeństwa.  
  
-   Adnotacji przezroczystości są wymuszane tylko w zestawie.  
  
-   Krytyczny dla zabezpieczeń typy i składniki musi użyć linkdemand, aby wymusić zabezpieczeń dla połączeń z poza zestaw.  
  
-   Reguły dziedziczenia nie są wymuszane.  
  
-   Istnieje możliwość dla kod o przezroczystym do wykonywania czynności szkodliwe uruchamianych w trybie pełnego zaufania.  
  
 [Powrót do początku](#top)  
  
<a name="enforcement"></a>   
## <a name="transparency-enforcement"></a>Egzekwowanie przejrzystości  
 Przezroczystość reguły nie są wymuszane, dopóki przezroczystość jest obliczana. W tym czasie <xref:System.InvalidOperationException> jest generowany, jeśli naruszenia reguły przezroczystość. Czas, który jest obliczana przezroczystość zależy od wielu czynników i nie można przewidzieć. Jest on obliczany możliwie najpóźniej. W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obliczenia przezroczystość poziomu zestawu występuje szybciej niż w .NET Framework 2.0. Tylko gwarancji jest, że przezroczystość obliczeń zostanie przeprowadzona w czasie, gdy są potrzebne. Jest to podobnie jak przy użyciu kompilatora just in time (JIT) można zmienić punktu, wykryto błędy w tej metodzie, gdy metoda ma być kompilowana. Obliczanie przezroczystość jest niewidoczny, jeśli kod nie zawiera błędów przezroczystość.  
  
## <a name="see-also"></a>Zobacz też  
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
