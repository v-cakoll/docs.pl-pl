---
title: 'Przewodnik: Emitowanie kodu w scenariuszach częściowo zaufanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection emit, anonymously hosted dynamic methods
- partial trust, reflection
- partial trust, emitting dynamic methods
- reflection emit, partial trust scenarios
- anonymously hosted dynamic methods [.NET Framework]
- emitting dynamic assemblies,partial trust scenarios
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0483f1477ee215537d1081fde791d0742d5aec50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793080"
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>Przewodnik: Emitowanie kodu w scenariuszach częściowo zaufanych
Odbicie emituje użycie tego samego interfejsu API, ustaw w pełnej lub częściowej relacji zaufania, ale niektóre funkcje wymagają specjalnych uprawnień w kodzie częściowo zaufanym. Ponadto emisji odbicia posiada funkcję, anonimowo obsługiwane metody dynamiczne, który jest przeznaczony do użycia z częściowej relacji zaufania, jak również przezroczyste dla zabezpieczeń zestawów.  
  
> [!NOTE]
>  Przed [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)], wymagany kod emisji <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> flagi. To uprawnienie jest zawarte domyślnie w `FullTrust` i `Intranet` zestawy nazwanych uprawnień, ale nie w `Internet` zestaw uprawnień. W związku z tym, biblioteka może być używana w częściowej relacji zaufania tylko wtedy, gdy miała <xref:System.Security.SecurityCriticalAttribute> atrybut i również wykonała <xref:System.Security.PermissionSet.Assert%2A> metodę <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Takie biblioteki wymagają weryfikacji zabezpieczeń zachowania ostrożność, ponieważ kodowanie błędów może spowodować luki w zabezpieczeniach. [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Pozwala kod był emitowany w scenariuszach częściowej relacji zaufania, bez wydawania żadnych wymogów bezpieczeństwa, ponieważ generowanie kodu nie jest z natury uprzywilejowaną operacją. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który emituje go. Dzięki temu biblioteki, które emitują kod zabezpieczenia przejrzysty i usuwa potrzebę zapewnienia <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, dzięki czemu bezpieczna biblioteka nie wymaga takiego przeglądu względem zabezpieczeń.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- [Definiowanie prostych piaskownic dla badania częściowo zaufanego kodu](#Setting_up).  
  
    > [!IMPORTANT]
    >  Jest to prosty sposób do eksperymentowania z kodem w częściowej relacji zaufania. Aby uruchomić kod, który rzeczywiście pochodzi z niezaufanych lokalizacji, zobacz [jak: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
- [Uruchamianie kodu w aplikacji częściowo zaufanych domen](#Running_code).  
  
- [Aby użyć anonimowo obsługiwanych metod dynamicznych do emisji i wykonania kodu w częściowej relacji zaufania](#Using_methods).  
  
 Aby uzyskać więcej informacji na temat emisji kodu w scenariuszach częściowej relacji zaufania, zobacz [problemy z zabezpieczeniami w emisji odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md).  
  
 Aby uzyskać pełną listę kodów pokazanych w tych procedurach, zobacz [sekcji z przykładowym](#Example) na końcu tego przewodnika.  
  
<a name="Setting_up"></a>   
## <a name="setting-up-partially-trusted-locations"></a>Definiowanie częściowo zaufanej lokalizacji  
 Dwie następujące procedury przedstawiają sposób ustawiania lokalizacji, z których można sprawdzić kod z częściowej relacji zaufania.  
  
- Pierwsza procedura pokazuje, jak utworzyć domenę aplikacji w trybie piaskownicy, w którym kod ma udzielone uprawnienia Internet.  
  
- Druga procedura pokazuje, jak dodać <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi do domeny aplikacji częściowo zaufanej, aby umożliwić dostęp do prywatnych danych w zestawach zaufania równej lub mniejszej.  
  
### <a name="creating-sandboxed-application-domains"></a>Tworzenie domen aplikacji w trybie piaskownicy  
 Aby utworzyć domenę aplikacji, w której Twoje zestawy są uruchamiane z częściowej relacji zaufania, należy określić zestaw uprawnień przyznawanych zestawów za pomocą <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia metody tworzenia domeny aplikacji. Najprostszym sposobem określenia przyznanego zestawu jest pobranie nazwanego zestawu z zasad zabezpieczeń.  
  
 Poniższa procedura tworzy domenę aplikacji w trybie piaskownicy, która uruchamia kod z częściowej relacji zaufania, aby przetestować scenariusze, w których emitowany kod może uzyskać dostęp tylko publiczne składowe typów publicznych. Dalsza procedura pokazuje sposób dodawania <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, aby przetestować scenariusze, w których emitowany kod może uzyskać dostęp do typów niepublicznych w zestawach, którym nadano uprawnienia równe lub mniejsze.  
  
##### <a name="to-create-an-application-domain-with-partial-trust"></a>Aby utworzyć domenę aplikacji z częściowym zaufaniem  
  
1. Utwórz zestaw uprawnień do przydzielenia do zestawów w domenie aplikacji w trybie piaskownicy. W tym przypadku jest używany zestaw uprawnień strefy Internet.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2. Utwórz <xref:System.AppDomainSetup> obiekt, aby zainicjować domenę aplikacji ze ścieżką do aplikacji.  
  
    > [!IMPORTANT]
    >  Dla uproszczenia ten przykład kodu używa bieżącego folderu. Aby uruchomić kod, który rzeczywiście pochodzi z Internetu, używaj oddzielnego folderu dla niezaufanego kodu zgodnie z opisem w [jak: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3. Utwórz domenę aplikacji, określając informacje o konfiguracji domeny aplikacji i przydziel zestaw dla wszystkich zestawów, które są wykonywane w domenie aplikacji.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     Ostatni parametr <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia metody umożliwia określenie zestawu zestawów, które mają być udzielone pełne zaufanie, a nie zestaw uprawnień w domenie aplikacji. Nie trzeba określać [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawów, które Twoja aplikacja używa, ponieważ te zestawy znajdują się w globalnej pamięci podręcznej. Zestawy w globalnej pamięci podręcznej są zawsze w pełni zaufane. Ten parametr służy do określenia zestawu o silnych nazwach, które nie znajdują się w globalnej pamięci podręcznej.  
  
### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Dodawanie RestrictedMemberAccess do domeny w trybie piaskownicy  
 Aplikacje hosta mogą umożliwić anonimowo obsługiwane metody dynamiczne mają mieć dostęp do prywatnych danych w zestawach posiadających poziomy zaufania równe lub mniejsze niż poziom zaufania zestawu, który emituje kod. Aby włączyć taką możliwość ograniczenia pominięcia testów widoczności usługi just-in-time (JIT), aplikacji hosta dodaje <xref:System.Security.Permissions.ReflectionPermission> obiekt z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi (RMA) do zestawu dotacji.  
  
 Na przykład host może udzielić uprawnień internetowych aplikacji internetowej i RMA, dzięki czemu aplikacja internetowa może emitować Kod, który uzyskuje dostęp do danych prywatnych w swoich własnych zestawach. Ponieważ dostęp jest ograniczony do zestawów równego lub mniejszego zaufania, aplikacja internetowa nie takich jak dostęp do elementów członkowskich całkowicie zaufanych zestawów [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawów.  
  
> [!NOTE]
>  Aby zapobiec podniesienie uprawnień, informacje stosu do montażu emitującego jest dołączana w przypadku anonimowo obsługiwane metody dynamiczne są zbudowane. Gdy metoda jest wywoływana, informacja stosu jest sprawdzana. W efekcie anonimowo obsługiwana metoda dynamiczna, która jest wywoływana z całkowicie zaufanego kodu jest nadal ograniczona do poziomu zaufania emitujące zgromadzenia.  
  
##### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Aby utworzyć domenę aplikacji z częściowym zaufaniem plus RMA  
  
1. Utwórz nową <xref:System.Security.Permissions.ReflectionPermission> obiekt z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (RMA) i użyj <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> metodę, aby dodać uprawnienie do zestawu dotacji.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     <xref:System.Security.PermissionSet.AddPermission%2A> Metoda dodaje uprawnienie do przyznanego zestawu, jeśli nie jest już włączona. Jeśli uprawnienie jest już uwzględniony w przydzielonym zestawie, określone flagi są dodawane do istniejącego uprawnienia.  
  
    > [!NOTE]
    >  RMA jest funkcją anonimowo obsługiwanych metod dynamicznych. W przypadku zwykłych metod dynamicznych Pomiń sprawdzanie widoczności JIT, emitowany kod wymaga pełnego zaufania.  
  
2. Utwórz domenę aplikacji, określając informacje o konfiguracji domeny aplikacji i przydziel zestawu.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## <a name="running-code-in-sandboxed-application-domains"></a>Uruchamianie kodu w trybie piaskownicy aplikacji domen  
 Poniższa procedura wyjaśnia, jak definiować klasy przy użyciu metod, które mogą być wykonywane w domenie aplikacji, jak utworzyć wystąpienia klasy w domenie i jak wykonać jej metody.  
  
#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Aby zdefiniować i wykonać metodę w domenie aplikacji  
  
1. Definiowanie klasy, która jest pochodną <xref:System.MarshalByRefObject>. Dzięki temu można utworzyć wystąpienia klasy w innych domenach aplikacji i wykonywać metody wywołań poza granice domeny aplikacji. Klasa w tym przykładzie ma nazwę `Worker`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2. Zdefiniuj metodę publiczną, która zawiera kod, który chcesz wykonać. W tym przykładzie kod emituje prostą metodę dynamiczną, tworzy delegata, aby wykonać metodę i wywołuje delegata.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3. W programie głównym Uzyskaj nazwę wyświetlaną zestawu. Ta nazwa jest używana podczas tworzenia wystąpienia elementu `Worker` klasy w domenie aplikacji w trybie piaskownicy.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4. W programie głównym Utwórz domenę aplikacji w trybie piaskownicy, zgodnie z opisem w [pierwszej procedury](#Setting_up) w tym przewodniku. Nie trzeba dodawać żadnych uprawnień do `Internet` zestawu uprawnień, ponieważ `SimpleEmitDemo` metoda wykorzystuje tylko metody publiczne.  
  
5. W programie głównym Utwórz wystąpienie obiektu `Worker` klasy w domenie aplikacji w trybie piaskownicy.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Metoda tworzy obiekt w docelowej domenie aplikacji i zwraca serwer proxy, który może służyć do wywołania właściwości i metod obiektu.  
  
    > [!NOTE]
    >  Jeśli używasz tego kodu w programie Visual Studio, należy zmienić nazwę klasy, aby uwzględnić przestrzeń nazw. Domyślnie przestrzeń nazw jest nazwą projektu. Na przykład jeśli projekt to "PartialTrust", nazwa klasy musi być "PartialTrust.Worker".  
  
6. Dodaj kod, aby wywołać `SimpleEmitDemo` metody. Wywołanie jest organizowane przez granicę domeny aplikacji, a kod jest wykonywany w domenie aplikacji w trybie piaskownicy.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## <a name="using-anonymously-hosted-dynamic-methods"></a>Aby użyć anonimowo obsługiwanych metod dynamicznych  
 Anonimowo obsługiwane metody dynamiczne są związane z przezroczystym zestawu, który jest udostępniany przez system. Dlatego, zawierają kod jest przezroczysty. Zwykłe metody dynamiczne, z drugiej strony, muszą być skojarzone z istniejącym modułem (czy bezpośrednio określone lub wywnioskowane na podstawie skojarzonego typu) i poziomu zabezpieczeń z tego modułu.  
  
> [!NOTE]
>  Jedynym sposobem, aby skojarzyć metodę dynamiczną z zestawem, który zapewnia hosting anonimowo jest użycie konstruktorów, które są opisane w poniższej procedurze. Nie można jawnie określić modułu w zestawie hostingu anonimowo.  
  
 Zwykłe metody dynamiczne mają dostęp do wewnętrznych członków modułu, z którymi są skojarzone z lub do prywatnych składowych typów, które są skojarzone. Ponieważ anonimowo obsługiwane metody dynamiczne są odizolowane od innego kodu, nie mają dostępu do prywatnych danych. Jednak mają ograniczone zdolności do pominięcia testów widoczności JIT w celu uzyskania dostępu do prywatnych danych. Ta możliwość jest ograniczona do zestawów, które mają poziomy zaufania równe lub mniejsze niż poziom zaufania zestawu, który emituje kod.  
  
 Aby zapobiec podniesienie uprawnień, informacje stosu do montażu emitującego jest dołączana w przypadku anonimowo obsługiwane metody dynamiczne są zbudowane. Gdy metoda jest wywoływana, informacja stosu jest sprawdzana. Anonimowo obsługiwana metoda dynamiczna, która jest wywoływana z całkowicie zaufanego kodu jest nadal ograniczona do poziomu zaufania zestawu, do którego została wyemitowana.  
  
#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Aby użyć anonimowo obsługiwanych metod dynamicznych  
  
- Utwórz anonimowo obsługiwaną metodę dynamiczną za pomocą konstruktora, który nie określa skojarzonego modułu lub typu.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     Jeśli anonimowo obsługiwana metoda dynamiczna używa tylko typy i metody publiczne, nie wymaga ograniczonego dostępu elementu członkowskiego i trzeba pomijać kontroli widoczność JIT.  
  
     Żadne specjalne ustawienia nie są wymagane do emitowania metody dynamicznej, ale emitowany kod wymaga uprawnień, które są wymagane przez typy i metody, które są używane. Na przykład, jeżeli emitowany kod wywołuje metodę, która uzyskuje dostęp do pliku, wymaga on <xref:System.Security.Permissions.FileIOPermission>. Jeśli poziom zaufania nie ma tego uprawnienia, wyjątek zabezpieczeń jest zgłaszany, gdy emitowany kod jest wykonywany. Kod przedstawiony tutaj emituje metodę dynamiczną, która używa tylko <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody. W związku z tym kod może być wykonywany z częściowo zaufanych lokalizacji.  
  
- Alternatywnie Utwórz anonimowo obsługiwaną metodę dynamiczną z ograniczoną możliwością pominięcia testów widoczności JIT, za pomocą <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> Konstruktor i określając `true` dla `restrictedSkipVisibility` parametru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     Ograniczenie jest takie, że anonimowo obsługiwana metoda dynamiczna dostęp do prywatnych danych tylko w zestawach z poziomów zaufania równe lub mniejsze niż poziom zaufania emitowanego zgromadzenia. Na przykład, jeśli metoda dynamiczna jest wykonywana z zaufanie do Internetu, jego dostęp do prywatnych danych w innych zestawach, które są również wykonywane z zaufaniem do Internetu, ale nie może uzyskać dostęp do prywatnych danych [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawów. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawy są zainstalowane w globalnej pamięci podręcznej i są zawsze w pełni zaufane.  
  
     Anonimowo obsługiwane metody dynamiczne mogą skorzystać z ograniczonej możliwości, aby pominąć kontrole widoczność JIT tylko wtedy, gdy aplikacja hosta udziela <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi. Żądanie tego uprawnienia następuje po wywołaniu metody.  
  
    > [!NOTE]
    >  Wywołaj informacje stosu dla uwzględnionego zestawu emitującego jest uwzględniony, podczas konstruowania metody dynamicznej. Dlatego przed uprawnieniami emitującymi Zgromadzenie a nie zestaw, który wywołuje metodę składa się zapotrzebowanie. Zapobiega to emitowany kod zostanie wykonywany z podwyższonym poziomem uprawnień.  
  
     [Pełny przykład kodu](#Example) na końcu tego instruktażu pokazano użycie i ograniczenia członków ograniczonego dostępu. Jego `Worker` klasa zawiera metodę, która może utworzyć anonimowo obsługiwane metody dynamiczne z lub bez ograniczonych możliwości pominięcia testów widoczności, a w przykładzie przedstawiono wynik wykonywania tej metody w domenach aplikacji, które mają różne poziomy zaufania.  
  
    > [!NOTE]
    >  Ograniczona zdolność do pominięcia widoczności kontroli jest funkcją anonimowo obsługiwanych metod dynamicznych. W przypadku zwykłych metod dynamicznych Pomiń sprawdzanie widoczności JIT, muszą otrzymać pełne zaufanie.  
  
<a name="Example"></a>   
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu demonstruje użycie <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> flagi, aby umożliwić anonimowo obsługiwanych metod dynamicznych, aby pominąć kontrole widoczność JIT, ale tylko wtedy, gdy docelowy element członkowski jest na równym lub mniejszym poziomie zaufania niż zestaw, który emituje kod.  
  
 W przykładzie zdefiniowano `Worker` klasy, które mogą być organizowane poza granice domeny aplikacji. Klasa ma dwa `AccessPrivateMethod` przeciążenia metody, które emitują i wykonują metody dynamiczne. Pierwsze przeciążenie emituje metodę dynamiczną, który wywołuje prywatną `PrivateMethod` metody `Worker` klasy i, to może emitować metodę dynamiczną z lub bez kontroli widoczności JIT. Drugie przeciążenie emituje metodę dynamiczną, która uzyskuje dostęp do `internal` właściwości (`Friend` właściwość w języku Visual Basic) z <xref:System.String> klasy.  
  
 W przykładzie użyto metody pomocnika, aby utworzyć przydzielony zestaw ograniczony do `Internet` uprawnień, a następnie tworzy domenę aplikacji za pomocą <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia metody, aby określić, że cały kod, który wykonuje w domenie używa tego zestawu dotacji. Przykład tworzy wystąpienie `Worker` klasy w domenie aplikacji i wykonuje `AccessPrivateMethod` metodę dwa razy.  
  
- Po raz pierwszy `AccessPrivateMethod` metoda jest wykonywana, sprawdzanie widoczności JIT są wymuszane. Metoda dynamiczna zawodzi, gdy jest wywoływana, ponieważ kontrole widoczność JIT uniemożliwiają dostęp do metody prywatnej.  
  
- Po raz drugi `AccessPrivateMethod` metoda jest wykonywana, sprawdzanie widoczności JIT jest pomijane. Metoda dynamiczna zawodzi, gdy jest ona kompilowana, ponieważ `Internet` przyznania zestaw nie przyznaje wystarczających uprawnień, aby pominąć kontrolę widoczności.  
  
 W przykładzie dodano <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> do przyznania zestaw. Przykład tworzy następnie drugą domenę, określając, że cały kod, który wykonuje w domenie ma udzielone uprawnienia w nowym przydzielonym zestawie. Przykład tworzy wystąpienie `Worker` klasy w domenie nowej aplikacji i wykonuje oba przeciążenia `AccessPrivateMethod` metody.  
  
- Pierwsze przeciążenie `AccessPrivateMethod` metody jest wykonywane i sprawdzenie widoczność JIT jest pomijane. Metoda dynamiczna kompiluje i wykonuje z powodzeniem, ponieważ zestaw, który emituje kod jest taki sam, jak zestaw, który zawiera metodę prywatną. W związku z tym poziomy zaufania są równe. Jeśli aplikacja, która zawiera `Worker` klasa miała kilka zestawów, ten sam proces powiedzie się dla każdego z tych zestawów, ponieważ wszystkie będą one będą na tym samym poziomie zaufania.  
  
- Drugie przeciążenie `AccessPrivateMethod` metody jest wykonywane i ponowne sprawdzenie widoczność JIT jest pomijane. Tym razem dynamiczna metoda nie działa, gdy jest ona kompilowana, ponieważ próbuje uzyskać dostęp do `internal` `FirstChar` właściwość <xref:System.String> klasy. Zestaw, który zawiera <xref:System.String> klasy jest w pełni zaufany. Dlatego jest na wyższym poziomie zaufania niż zestaw, który emituje kod.  
  
 Porównanie to pokazuje jak <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> włącza częściowo zaufany kod, aby pominąć widoczność sprawdza, czy innego częściowo zaufanego kodu bez narażania bezpieczeństwa zaufanego kodu.  
  
### <a name="code"></a>Kod  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Jeśli tworzysz ten przykład kodu w programie Visual Studio, należy zmienić nazwę klasy, aby uwzględnić przestrzeń nazw, jeśli przekazujesz go do <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> metody. Domyślnie przestrzeń nazw jest nazwą projektu. Na przykład jeśli projekt to "PartialTrust", nazwa klasy musi być "PartialTrust.Worker".  
  
## <a name="see-also"></a>Zobacz także

- [Problemy związane z zabezpieczeniami w emisji odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)
- [Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
