---
title: "Wskazówki: emitowanie kodu w scenariuszach częściowo zaufanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 121dfd91d797aa03860abd4404ffe20113e70f85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-emitting-code-in-partial-trust-scenarios"></a>Wskazówki: emitowanie kodu w scenariuszach częściowo zaufanych
Emisja odbicia używa tego samego interfejsu API w pełnej lub częściowej relacji zaufania, ale niektóre funkcje wymagają szczególnych uprawnień w częściowo zaufany kod. Ponadto emisja odbicia ma funkcji hostowanej anonimowo metody dynamicznej, który jest przeznaczony do użycia z częściowa relacja zaufania i zestawy przezroczystym poziomie bezpieczeństwa.  
  
> [!NOTE]
>  Przed [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)], emitowanie kodu wymagane <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit?displayProperty=nameWithType> flagi. To uprawnienie jest domyślnie włączone w `FullTrust` i `Intranet` ustawia uprawnienia nazwanego, ale nie w `Internet` zestaw uprawnień. W związku z tym biblioteki można używać z częściowa relacja zaufania tylko w przypadku, gdyby <xref:System.Security.SecurityCriticalAttribute> atrybutu i również wykonywane <xref:System.Security.PermissionSet.Assert%2A> metodę <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>. Takie biblioteki wymagają przeglądu zabezpieczeń zachować ostrożność, ponieważ błędy kodowania może skutkować luk w zabezpieczeniach. [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] Umożliwia kod, aby emitować w scenariuszach częściowo zaufanych bez wystawiania wszystkie żądania kontroli zabezpieczeń, ponieważ generowanie kodu nie jest z założenia uprzywilejowanych operacji. Oznacza to, że wygenerowany kod nie ma więcej uprawnień niż zestaw, który emituje go. Dzięki temu biblioteki, w których Emituj kod jest przezroczystym poziomie bezpieczeństwa i eliminuje potrzebę do potwierdzenia <xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>, dzięki czemu zapisywania bezpiecznego biblioteki nie wymaga przeglądu względem zabezpieczeń.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   [Konfigurowanie prostego piaskownicy testowania częściowo zaufany kod](#Setting_up).  
  
    > [!IMPORTANT]
    >  Jest to prosty sposób na wypróbowanie kodu w częściowej relacji zaufania. Aby uruchomić kod, który faktycznie pochodzi z niezaufanej lokalizacji, zobacz [porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
-   [Uruchamianie kodu w aplikacji częściowo zaufanej domeny](#Running_code).  
  
-   [Przy użyciu anonimowo hostowane metody dynamiczne Emituj i wykonanie kodu w częściowej relacji zaufania](#Using_methods).  
  
 Aby uzyskać więcej informacji na temat emitowanie kodu w scenariuszach częściowo zaufanych, zobacz [problemy z zabezpieczeniami w emisji odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md).  
  
 Aby uzyskać pełną listę kodem przedstawionym w tych procedurach, zobacz [przykład sekcji](#Example) na końcu tego przewodnika.  
  
<a name="Setting_up"></a>   
## <a name="setting-up-partially-trusted-locations"></a>Konfigurowanie częściowo zaufanych lokalizacji  
 Poniższe dwie procedury pokazują, jak skonfigurować lokalizacje, z których można sprawdzić kod w częściowej relacji zaufania.  
  
-   Pierwsza procedura przedstawia sposób tworzenia domeny aplikacji w trybie piaskownicy, w którym kod jest uprawnień internetowych.  
  
-   Druga procedura przedstawia sposób dodawania <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Flaga aplikacji częściowo zaufanej domeny, aby włączyć dostęp do danych w zestawach zaufania równa lub mniejsza.  
  
### <a name="creating-sandboxed-application-domains"></a>Tworzenie domeny aplikacji w trybie piaskownicy  
 Aby utworzyć domenę aplikacji, w którym są uruchomione ponownie zestawy z częściowa relacja zaufania, należy podać zestaw uprawnień, aby można mu było przydzielić do zestawów przy użyciu <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenie metody tworzenia domeny aplikacji. Najprostszym sposobem, aby określić zestaw uprawnień jest można pobrać zestawu z zasad zabezpieczeń o nazwie uprawnień.  
  
 Poniższa procedura dotyczy tworzenia domeny aplikacji w trybie piaskownicy, która uruchamia kod z częściowej relacji zaufania, aby przetestować scenariusze, w których emitowany kodu można uzyskać dostęp tylko publiczne elementy członkowskie typy publiczne. Kolejne procedury przedstawiono sposób dodawania <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>, aby przetestować scenariusze, w których emitowany kodu można uzyskać dostępu do niepubliczne typy i składniki w zestawy, które są przyznawane uprawnienia równa lub mniejsza.  
  
##### <a name="to-create-an-application-domain-with-partial-trust"></a>Aby utworzyć domenę aplikacji z częściowa relacja zaufania  
  
1.  Utwórz uprawnienia do zestawów w domenie aplikacji piaskownicy. W takim przypadku służy strefy Internetu zestaw uprawnień.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2.  Utwórz <xref:System.AppDomainSetup> obiekt do zainicjowania domeny aplikacji z ścieżkę aplikacji.  
  
    > [!IMPORTANT]
    >  Dla uproszczenia w tym przykładzie kodu używane bieżącego folderu. Aby uruchomić kod, który faktycznie pochodzą z Internetu, używać oddzielnego folderu dla niezaufanych kodu, zgodnie z opisem w [porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3.  Tworzenie domeny aplikacji, określania informacji o konfiguracji domeny aplikacji i grant dla wszystkich zestawów, które są wykonywane w domenie aplikacji.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     Ostatni parametr <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenie metody można określić zbiór zestawów, które będą mieli pełne zaufanie, zamiast zestawu domeny aplikacji. Nie trzeba określać [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawy, które Twoja aplikacja używa, ponieważ te zestawy są w globalnej pamięci podręcznej zestawów. Zestawów w globalnej pamięci podręcznej zestawów są zawsze całkowicie zaufane. Ten parametr umożliwia określenie zestawy o silnych nazwach, które nie znajdują się w globalnej pamięci podręcznej zestawów.  
  
### <a name="adding-restrictedmemberaccess-to-sandboxed-domains"></a>Dodawanie RestrictedMemberAccess do domeny w trybie piaskownicy  
 Można zezwolić na obsługę aplikacji hostowanej anonimowo metody dynamicznej mają dostęp do danych w zestawach, do których poziomy zaufania równa lub mniejsza niż poziom zaufania zestawu, który emituje kod. Aby włączyć tę możliwość ograniczone do pominięcia just in time (JIT) widoczność kontroli, dodaje aplikacji hosta <xref:System.Security.Permissions.ReflectionPermission> obiekt z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi zestawu (autoryzacji).  
  
 Na przykład host może udzielić uprawnienia Internet aplikacji internetowych oraz autoryzacji, dzięki czemu aplikacji internetowej można wyemitować kodu, który uzyskuje dostęp do danych prywatnych w ich własnych zestawach. Ponieważ dostęp jest ograniczony do zestawów zaufania równa lub mniejsza, aplikację internetową nie takich jak dostęp do elementów członkowskich całkowicie zaufanych zestawów [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawów.  
  
> [!NOTE]
>  Aby zapobiec podniesienie uprawnień, informacje stosu dla zestawu emisji jest dołączana w przypadku zbudowanych hostowanej anonimowo metody dynamicznej. Po wywołaniu metody informacje stosu jest zaznaczone. W związku z tym hostowanej anonimowo metody dynamicznej, który jest wywoływany z całkowicie zaufanego kodu jest nadal ograniczone do poziomu zaufania emisji zestawu.  
  
##### <a name="to-create-an-application-domain-with-partial-trust-plus-rma"></a>Aby utworzyć domenę aplikacji z częściowa relacja zaufania oraz autoryzacji  
  
1.  Utwórz nową <xref:System.Security.Permissions.ReflectionPermission> obiekt z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> (autoryzacji) Flaga i użyj <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=nameWithType> metody, aby dodać uprawnienia do zestaw uprawnień.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     <xref:System.Security.PermissionSet.AddPermission%2A> Metoda dodaje uprawnienia grant ustawić, jeśli nie jest już dołączony. Jeśli uprawnienie jest już uwzględniony w zestawie grant, określone flagi są dodawane do istniejących uprawnień.  
  
    > [!NOTE]
    >  Autoryzacji jest funkcją hostowanej anonimowo metody dynamicznej. W przypadku zwykłej metod dynamicznych pominąć sprawdzanie widoczność JIT, emitowany kodu wymaga pełnego zaufania.  
  
2.  Tworzenie domeny aplikacji, określania informacji o konfiguracji domeny aplikacji i przyznania ustawić.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## <a name="running-code-in-sandboxed-application-domains"></a>Uruchamianie kodu w trybie piaskownicy aplikacji domenach  
 W poniższej procedurze wyjaśniono, jak można zdefiniować klasę przy użyciu metod, które mogą być wykonywane w domenie aplikacji, jak można utworzyć wystąpienia klasy w domenie i jak wykonać jego metody.  
  
#### <a name="to-define-and-execute-a-method-in-an-application-domain"></a>Aby zdefiniować i wykonania metody w domenie aplikacji  
  
1.  Definiowanie klasy, która jest pochodną <xref:System.MarshalByRefObject>. Dzięki temu można utworzyć wystąpienia klasy w innych domenach aplikacji i do wykonywania wywołań metody poza granice domeny aplikacji. Nosi nazwę klasy w tym przykładzie `Worker`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2.  Zdefiniuj metodę publiczną, która zawiera kod, który chcesz wykonać. W tym przykładzie kodu emituje to prosta metoda dynamicznych, tworzy delegata można wykonać metody i wywołuje delegata.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3.  W programie głównego ustalić nazwę wyświetlaną z zestawu. Ta nazwa jest używana podczas tworzenia wystąpienia `Worker` klasy w domenie aplikacji piaskownicy.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4.  W programie głównego tworzenia domeny aplikacji w trybie piaskownicy, zgodnie z opisem w [Pierwsza procedura](#Setting_up) w tym przewodniku. Nie masz uprawnień do dodawania `Internet` ustawić uprawnienia, ponieważ `SimpleEmitDemo` metoda używa tylko metody publiczne.  
  
5.  W programie główne utworzenia wystąpienia `Worker` klasy w domenie aplikacji piaskownicy.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Metoda tworzy obiekt w docelowej domenie aplikacji i zwraca serwera proxy, który może służyć do wywołania, właściwości i metody obiektu.  
  
    > [!NOTE]
    >  Jeśli używasz tego kodu w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], należy zmienić nazwę klasy, aby uwzględnić przestrzeni nazw. Domyślnie przestrzeń nazw jest nazwa projektu. Na przykład jeśli projekt jest "PartialTrust", nazwa klasy musi być "PartialTrust.Worker".  
  
6.  Dodaj kod, aby wywołać `SimpleEmitDemo` metody. Wywołanie jest organizowanego między granicami domeny aplikacji i kod jest wykonywany w domenie aplikacji piaskownicy.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## <a name="using-anonymously-hosted-dynamic-methods"></a>Przy użyciu anonimowo hostowane metody dynamiczne  
 Hostowanej anonimowo metody dynamicznej są skojarzone z przezroczystym zestawu, który jest udostępniany przez system. W związku z tym kodu, które zawierają jest niewidoczny. Zwykłe metody dynamiczne, z drugiej strony, musi być skojarzony z istniejący moduł (na bezpośrednio określony lub wywnioskować na podstawie skojarzonego typu) i wykonać ich poziom zabezpieczeń z tego modułu.  
  
> [!NOTE]
>  Jedynym sposobem, aby skojarzyć dynamiczne — metoda z zestawu, który udostępnia hosting anonimowego jest użyj konstruktorów, które zostały opisane w poniższej procedurze. Nie można jawnie określić moduł w zestawie hostingu anonimowe.  
  
 Zwykłe metod dynamicznych ma dostęp do wewnętrznych elementów członkowskich moduł, który skojarzonych z nimi, lub prywatne elementy członkowskie tego typu, które są skojarzone. Ponieważ hostowanej anonimowo metody dynamicznej są odizolowane od innego kodu, nie mają dostępu do danych. Jednak mają ograniczone możliwości Aby pominąć sprawdzanie widoczność JIT do uzyskania dostępu do danych. Ta możliwość jest ograniczona do zestawów, które mają poziomy zaufania równa lub mniejsza niż poziom zaufania zestawu, który emituje kod.  
  
 Aby zapobiec podniesienie uprawnień, informacje stosu dla zestawu emisji jest dołączana w przypadku zbudowanych hostowanej anonimowo metody dynamicznej. Po wywołaniu metody informacje stosu jest zaznaczone. Hostowanej anonimowo metody dynamicznej, który jest wywoływany z całkowicie zaufanego kodu jest nadal ograniczone do zestawu, który go wysyłanego poziom zaufania.  
  
#### <a name="to-use-anonymously-hosted-dynamic-methods"></a>Aby użyć anonimowo hostowane metody dynamiczne  
  
-   Tworzenie hostowanej anonimowo metody dynamicznej za pomocą konstruktora, który nie określa skojarzone modułu lub typu.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     Jeśli hostowanej anonimowo metody dynamicznej używane są tylko typy publiczne i metody, nie wymaga dostępu do elementu członkowskiego ograniczonym i nie ma pomijania sprawdzania widoczność JIT.  
  
     Żadne specjalne uprawnienia są wymagane do emisji dynamicznego metody, ale emitowany kod wymaga uprawnienia, które są wymagane przez typy i metody, które są używane. Na przykład, jeśli emitowany kod wywołuje metodę, która uzyskuje dostęp do pliku, wymaga <xref:System.Security.Permissions.FileIOPermission>. Jeśli poziom zaufania nie ma te uprawnienia, wyjątek zabezpieczeń jest generowany po emitowany kod jest wykonywany. Dynamiczne metody, która używa tylko emituje kod pokazane <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody. W związku z tym można wykonać kod z częściowo zaufanych lokalizacji.  
  
-   Można również utworzyć hostowanej anonimowo metody dynamicznej z ograniczeniami możliwość pominąć sprawdzanie widoczność JIT, za pomocą <xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> Konstruktor i określanie `true` dla `restrictedSkipVisibility` parametru.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     Ograniczenie to, że hostowanej anonimowo metody dynamicznej mają dostęp do danych prywatnych tylko w zestawach z poziomami zaufania równa lub mniejsza niż poziom zaufania emisji zestawu. Na przykład, jeśli wykonanie metody dynamicznej z Internetu zaufania, można uzyskać dostępu do danych prywatnych w innych zestawów, które także są wykonywane z zaufaniem Internet, ale nie ma dostępu do danych prywatnych od [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawów. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]zestawy są zainstalowane w globalnej pamięci podręcznej zestawów i są zawsze w pełni zaufany.  
  
     Hostowanej anonimowo metody dynamicznej można pominąć JIT widoczność kontroli tylko wtedy, gdy aplikacja hosta udziela za pomocą tej funkcji ograniczeniami <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi. Żądanie w celu uzyskania tego uprawnienia następuje po wywołaniu metody.  
  
    > [!NOTE]
    >  Informacje stosu wywołań dla zestawu emisji jest dołączana w przypadku metody dynamicznej jest tworzony. W związku z tym żądanie jest wykonywana przed uprawnienia emisji zestawu zamiast zestawu, który wywołuje metodę. Uniemożliwia to emitowany kod wykonywany z podwyższonym poziomem uprawnień.  
  
     [Pełny przykład kodu](#Example) na końcu tego przewodnika przedstawia użycie i ograniczenia dostępu do elementu członkowskiego ograniczone. Jego `Worker` klasa zawiera metodę, którą może utworzyć hostowanej anonimowo metody dynamicznej z lub bez ograniczone możliwości pominąć sprawdzanie widoczność i przykładzie wynik wykonania tej metody w domenach aplikacji, które mają różne poziomy zaufania.  
  
    > [!NOTE]
    >  Ograniczona możliwość pominąć sprawdzanie widoczność jest funkcją hostowanej anonimowo metody dynamicznej. W przypadku zwykłej metod dynamicznych pominąć sprawdzanie widoczność JIT, ich musi mieć przyznane pełne zaufanie.  
  
<a name="Example"></a>   
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje użycie <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> flagę anonimowo hostowane metody dynamiczne, aby pominąć sprawdzanie widoczność JIT, ale tylko wtedy, gdy element docelowy jest na poziomie zaufania niż zestaw, który emituje kod równa lub mniejsza.  
  
 W przykładzie zdefiniowano `Worker` klasy, które mogą być przekazywane między granicami domeny aplikacji. Klasa ma dwa `AccessPrivateMethod` przeciążenia metody, które Emituj i wykonywanie metod dynamicznych. Pierwszy przeciążenia emituje dynamiczne metodę, która wywołuje prywatna `PrivateMethod` metody `Worker` klasy i może emitować metody dynamicznej z lub bez kontroli widoczność JIT. Drugi przeciążenia emituje dynamiczne metodę, która uzyskuje dostęp do `internal` właściwości (`Friend` właściwość w języku Visual Basic) z <xref:System.String> klasy.  
  
 W przykładzie użyto metody pomocniczej, aby utworzyć zestaw ograniczone do uprawnień `Internet` uprawnienia, a następnie tworzy domenę aplikacji przy użyciu <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenie metody, aby określić, że cały kod, który wykonuje w domenie korzysta z tego zestawu. W przykładzie jest tworzony wystąpienia `Worker` klasy w domenie aplikacji, a następnie wykonuje `AccessPrivateMethod` metody dwa razy.  
  
-   Po raz pierwszy `AccessPrivateMethod` metoda jest wykonywana, JIT widoczność kontroli są wymuszane. Metody dynamicznej kończy się niepowodzeniem podczas jest wywoływana, ponieważ kontroli widoczność JIT uniemożliwić dostęp do metody prywatnej.  
  
-   Po raz drugi `AccessPrivateMethod` metoda jest wykonywana, są pomijane sprawdzanie widoczność JIT. Metody dynamicznej nie działa, gdy jest on skompilowany, ponieważ `Internet` przyznać zestawu nie powoduje przyznania wystarczających uprawnień, aby pominąć sprawdzanie widoczności.  
  
 W przykładzie dodano <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> udzielania ustawić. Tworzona jest następnie druga domena, określający, że cały kod, który jest wykonywany w domenie otrzymuje uprawnienia w nowym zestawie grant. W przykładzie jest tworzony wystąpienia `Worker` klasy w nowej domenie aplikacji, a następnie wykonuje zarówno przeciążeń `AccessPrivateMethod` metody.  
  
-   Pierwszy przeciążenia `AccessPrivateMethod` metoda jest wykonywana i widoczności JIT sprawdza są pomijane. Metody dynamicznej kompiluje i wykonuje pomyślnie, ponieważ zestaw, który emituje kod jest taka sama jak zestaw zawierający Metoda prywatna. W związku z tym poziomy zaufania są takie same. Jeśli aplikacja zawiera `Worker` klasa ma kilka zestawów, ten sam proces powiedzie się dla każdego z tych zestawów, ponieważ wszystkie się na tym samym poziomie zaufania.  
  
-   Drugi przeciążenia `AccessPrivateMethod` metoda jest wykonywana, a następnie ponownie widoczność JIT sprawdza są pomijane. Teraz metody dynamicznej nie powiedzie się, gdy jest on skompilowany, ponieważ próbuje uzyskać dostęp `internal` `FirstChar` właściwość <xref:System.String> klasy. Zestaw zawierający <xref:System.String> klasy jest w pełni zaufany. W związku z tym jest na wyższym poziomie zaufania niż zestaw, który emituje kod.  
  
 To porównanie pokazuje sposób <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> umożliwia częściowo zaufany kod, aby pominąć widoczność sprawdza, czy inne częściowo zaufanego kodu bez uszczerbku dla bezpieczeństwa zaufanego kodu.  
  
### <a name="code"></a>Kod  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   W przypadku tworzenia tym przykładzie kodu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], należy zmienić nazwę klasy do dołączenia przestrzeni nazw, gdy przekaż go do <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> metody. Domyślnie przestrzeń nazw jest nazwa projektu. Na przykład jeśli projekt jest "PartialTrust", nazwa klasy musi być "PartialTrust.Worker".  
  
## <a name="see-also"></a>Zobacz też  
 [Emituj problemy z zabezpieczeniami w odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 [Porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
