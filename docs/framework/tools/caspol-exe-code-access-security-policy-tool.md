---
title: "Caspol.exe (Narzędzie zasad zabezpieczeń dostępu kodu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permission sets, modifying security policy
- security policy [.NET Framework], Code Access Security Policy tool
- enterprise security policy
- referencing code groups and permission sets
- user security policy
- Caspol.exe
- Code Access Security Policy tool
- code groups, modifying security policy
- application development [.NET Framework], security
- machine security policy
- security policy [.NET Framework], modifying
- manually editing security configuration files
ms.assetid: d2bf6123-7b0c-4e60-87ad-a39a1c3eb2e0
caps.latest.revision: "44"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ab363e833ecde86a17d9adea3fcd26351725868
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Narzędzie zasad zabezpieczeń dostępu kodu)
Narzędzie (Caspol.exe) sprawdzania zabezpieczeń dostępu kodu (CAS) pozwala użytkownikom i administratorom na modyfikowanie zasad bezpieczeństwa na poziomie zasad komputera, na poziomie zasad użytkownika i na poziomie zasad przedsiębiorstwa.  
  
> [!IMPORTANT]
>  Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Caspol.exe nie wpływa na zasady CAS, chyba że [ \<legacyCasPolicy > element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ma ustawioną wartość `true`. Wszelkie ustawienia pokazywane lub modyfikowane przez narzędzie CasPol.exe wpływają tylko na aplikacje, w których są stosowane zasady CAS. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
> [!NOTE]
>  Na komputerach 64-bitowych dostępne są obie, 32-bitowa i 64-bitowa, wersje zasad zabezpieczeń. Aby upewnić się, że zmiany zasad mają zastosowanie do obu, 32-bitowych i 64-bitowych aplikacji, należy uruchomić obie, 32-bitową i 64-bitową, wersję Caspol.exe.  
  
 Narzędzie sprawdzania zabezpieczeń dostępu kodu jest automatycznie instalowane z .NET Framework i z programem Visual Studio. Caspol.exe można znaleźć w %windir%\Microsoft.NET\Framework\\*wersji* w systemach 32-bitowych lub %windir%\Microsoft.NET\Framework64\\*wersji* w systemach 64-bitowych. (Na przykład lokalizacja to %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe dla .NET Framework 4 w systemach 64-bitowych). Może być zainstalowanych wiele wersji narzędzia, jeżeli komputer używa równolegle wielu wersji platformy .NET Framework. Narzędzie można uruchomić z katalogu instalacji. Jednak zaleca się używanie [polecenie monituje o](../../../docs/framework/tools/developer-command-prompt-for-vs.md), która nie wymaga przejść do folderu instalacji.  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
caspol [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-af** *assembly_file*|Dodaje zestaw, który implementuje niestandardowy obiekt zabezpieczeń (taki jak niestandardowe uprawnienia lub niestandardowe warunki członkostwa), do listy zestawów o pełnym zaufaniu dla specyficznego poziomu zasad. *Assembly_file* argument określa zestaw do dodania. Ten plik musi być podpisany z [silnej nazwy](../../../docs/framework/app-domains/strong-named-assemblies.md). Możesz utworzyć zestaw o silnej nazwie przy użyciu [silnej nazwy narzędzia (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).<br /><br /> Za każdym razem, gdy zestaw uprawnień zawierający niestandardowe uprawnienia jest dodawany do zasad, zestaw implementujący niestandardowe uprawnienia musi zostać dodany do listy zestawów o pełnym zaufaniu dla danego poziomu zasad. Zestawy, które implementują niestandardowe obiekty zabezpieczeń (takie jak niestandardowe grupy kodu lub warunki członkostwa) używane w zasadach zabezpieczeń (takich jak zasady komputera) powinny być zawsze dodawane do listy zestawów pełnego zaufania. **Uwaga:** Jeśli zestaw implementujący niestandardowe obiekty bezpieczeństwa odwołuje się do innych zestawów, należy najpierw dodać zestawów występujących w odwołaniach do listy zestawu pełnego zaufania. Niestandardowe obiekty zabezpieczeń stworzone za pomocą języków Visual Basic, C++ i JScript odwołują się odpowiednio do Microsoft.VisualBasic.dll, Microsoft.VisualC.dll lub Microsoft.JScript.dll. Zestawy te nie znajdują się domyślnie na liście zestawów o pełnym zaufaniu. Należy dodać odpowiedni zestaw do listy o pełnym zaufaniu przed dodaniem niestandardowego obiektu zabezpieczeń. Niewykonanie tej czynności spowoduje awarię systemu zabezpieczeń, powodując niepowodzenie ładowania zestawów. W takiej sytuacji Caspol.exe **-all - Zresetuj** opcja nie będzie naprawić zabezpieczeń. W celu naprawienia zabezpieczeń należy ręcznie wyedytować pliki zabezpieczeń, aby usunąć niestandardowy obiekt zabezpieczeń.|  
|**-addgroup** {*nazwa_grupy_nadrzędnej &#124; parent_name*} *nazwa_zestawu_uprawnień członkostwo* [*flagi*]<br /><br /> lub<br /><br /> **-ag** {*nazwa_grupy_nadrzędnej &#124; parent_name*} *nazwa_zestawu_uprawnień członkostwo* [*flagi*]|Dodaje nową grupę kodu do hierarchii grup kodu. Można określić *nazwa_grupy_nadrzędnej* lub *parent_name*. *Nazwa_grupy_nadrzędnej* argument określa etykiety (na przykład 1. lub 1.1.) grupy kodów, który jest elementem nadrzędnym grupy kodów dodawany. *Parent_name* argument określa nazwę grupy kodu, który jest elementem nadrzędnym grupy kodów dodawany. Ponieważ *nazwa_grupy_nadrzędnej* i *parent_name* mogą być używane zamiennie, Caspol.exe musi mieć możliwość rozróżnienia między nimi. W związku z tym *parent_name* nie może rozpoczynać się cyfrą. Ponadto *parent_name* może zawierać tylko A-Z, 0-9 i znaków podkreślenia.<br /><br /> *Członkostwo* argument określa warunek członkostwa dla nowej grupy kodu. Aby uzyskać więcej informacji, zobacz tabelę *członkostwo* argumenty w dalszej części tej sekcji.<br /><br /> *Nazwa_zestawu_uprawnień* argument jest nazwą zestawu uprawnień, która zostanie skojarzona z nową grupą kodu. Można również ustawić co najmniej jeden *flagi* dla nowej grupy. Aby uzyskać więcej informacji, zobacz tabelę *flagi* argumenty w dalszej części tej sekcji.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> lub<br /><br /> **-region** {*o nazwie*_*psfile* &#124; *psfile* *nazwa_zestawu_uprawnień*}|Dodaje nowy, nazwany zestaw uprawnień do zasad. Zestaw uprawnień musi być w formacie XML i być zapisany w pliku xml. Jeśli plik XML zawierający nazwę uprawnienia ustawić, tylko ten plik (*psfile*) został określony. Jeśli plik XML nie zawiera nazwy zestawu uprawnień, należy określić zarówno nazwę pliku XML (*psfile*) i nazwa zestawu uprawnień (*nazwa_zestawu_uprawnień*).<br /><br /> Należy zauważyć, że wszystkie uprawnienia użyte w zestawie uprawnień muszą być zdefiniowane w zestawie zawartym w globalnej pamięci podręcznej zestawów.|  
|**-a**[**ll**]|Wskazuje, że wszystkie opcje następujące po niej mają zastosowanie do zasad komputera, użytkownika i przedsiębiorstwa. **— Wszystkie** opcja zawsze odwołuje się do zasad aktualnie zalogowanego użytkownika. Zobacz **- customall** opcję, aby odwoływać się do zasad użytkownika użytkownika innego niż bieżący użytkownik.|  
|**-chggroup** {*etykiety &#124; nazwa*} {*członkostwo* &#124; *nazwa_zestawu_uprawnień* &#124;<br /><br /> *flagi*`}`<br /><br /> lub<br /><br /> **-cg** {*etykiety &#124; nazwa*} {*członkostwo* &#124; *nazwa_zestawu_uprawnień* &#124;<br /><br /> *flagi*`}`|Zmienia warunek członkostwa grupy kodów, zestaw uprawnień lub ustawień **wyłącznego**, **levelfinal**, **nazwa**, lub **opis**flagi. Można określić *etykiety* lub *nazwa*. *Etykiety* argument określa etykiety (na przykład 1. lub 1.1.) grupy kodów. *Nazwa* argument określa nazwę grupy kod, aby zmienić. Ponieważ *etykiety* i *nazwa* mogą być używane zamiennie, Caspol.exe musi mieć możliwość rozróżnienia między nimi. W związku z tym *nazwa* nie może rozpoczynać się cyfrą. Ponadto *nazwa* może zawierać tylko A-Z, 0-9 i znaków podkreślenia.<br /><br /> *Nazwa_zestawu_uprawnień* argument określa nazwę zestawu do skojarzenia z grupy kodu uprawnień. Zobacz tabelę w dalszej części tej sekcji, aby uzyskać informacje na *członkostwo* i *flagi* argumentów.|  
|**-chgpset***nazwa_zestawu_uprawnień psfile* <br /><br /> lub<br /><br /> **-cp** *nazwa_zestawu_uprawnień psfile*|Zmienia nazwany zestaw uprawnień. *Psfile* argument dostarcza nową definicję dla zestawu uprawnień; jest to plik zestawu serializacji uprawnień w formacie XML. *Nazwa_zestawu_uprawnień* argument określa nazwę chcesz zmienić zestaw uprawnień.|  
|**-customall***ścieżki* <br /><br /> lub<br /><br /> **-ca***ścieżki* |Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do zasad komputera, przedsiębiorstwa i określonych niestandardowych zasad użytkownika. Należy określić lokalizację użytkownika niestandardowego pliku konfiguracji zabezpieczeń z *ścieżki* argumentu.|  
|**-cu**[**stomuser**] *ścieżki*|Umożliwia administrację niestandardowymi zasadami użytkownika, które nie należą do użytkownika, w którego imieniu program Caspol.exe jest aktualnie uruchomiony. Należy określić lokalizację użytkownika niestandardowego pliku konfiguracji zabezpieczeń z *ścieżki* argumentu.|  
|**-enterprise**<br /><br /> lub<br /><br /> **-en**|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad przedsiębiorstwa. Użytkownicy, którzy nie są administratorami przedsiębiorstwa, nie posiadają wystarczających praw, aby modyfikować zasady przedsiębiorstwa, jednak mogą je wyświetlać. W scenariuszach bez przedsiębiorstwa zasady te domyślnie nie kolidują z zasadami komputera i użytkownika.|  
|**-e**[**xecution**] {**na** &#124; **poza**}|Włącza lub wyłącza mechanizm sprawdzający uprawnienia uruchamiania przed rozpoczęciem wykonywania kodu. **Uwaga:** tego przełącznika zostanie usunięta w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).|  
|**-f**[**orce**]|Pomija test samolikwidacji narzędzia i zmienia zasady określone przez użytkownika. Normalnie Caspol.exe sprawdza, czy dowolne zmiany zasad mogą uniemożliwić programowi Caspol.exe poprawne działanie; jeśli tak, Caspol.exe nie zapisze zmian zasad i wyświetli komunikat o błędzie. Aby wymusić Caspol.exe zmiany zasad, nawet wtedy, gdy zapobiega to Caspol.exe się uruchamianie, użyj **— wymusić** opcji.|  
|**-h**[**elp**]|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
|**-l**[**ist**]|Wypisuje hierarchię grup kodu i zestawy uprawnień dla określonego komputera, użytkownika, przedsiębiorstwa lub wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listdescription**<br /><br /> lub<br /><br /> **-ld**|Wypisuje opisy wszystkich grup kodu dla określonego poziomu zasad.|  
|**-listfulltrust**<br /><br /> lub<br /><br /> **-lf**|Wypisuje zawartość listy zestawów o pełnym zaufaniu dla określonego poziomu zasad.|  
|**-listgroups**<br /><br /> lub<br /><br /> **-lg**|Wypisuje grupy kodu dla określonego poziomu zasad lud dla wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listpset Wyświetla** lub **-lp**|Wyświetla zestawy uprawnień dla określonego poziomu zasad lub poziomów zasad.|  
|**-m**[**achine**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad komputera. Użytkownicy, którzy nie są administratorami, nie posiadają wystarczających praw, aby modyfikować zasady komputera, jednak mogą je wyświetlać. Dla administratorów **-machine** jest ustawieniem domyślnym.|  
|**-polchgprompt** {**na** &#124; **poza**}<br /><br /> lub<br /><br /> **-PZ** {**na** &#124; **poza**}|Włącza lub wyłącza monit, który jest wyświetlany zawsze, gdy Caspol.exe jest uruchamiany z opcją powodującą zmianę zasad.|  
|**-quiet**<br /><br /> lub<br /><br /> **-q**|Tymczasowo wyłącza monit, który jest normalnie wyświetlany dla opcji powodującej zmianę zasad. Globalne ustawienie monitu nie jest zmieniane. Należy użyć tej opcji w pojedynczym poleceniu, aby uniknąć wyłączenia monitu dla wszystkich poleceń Caspol.exe.|  
|**-r**[**ecover**]|Odzyskuje zasady z pliku kopii zapasowej. Zawsze, gdy zmieniane są zasady, Caspol.exe zapisuje stare zasady w pliku kopii zapasowej.|  
|**-remfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-rf***assembly_file* |Usuwa zestaw z listy zestawów o pełnym zaufaniu poziomu zasad. Ta operacja powinna być wykonana, jeśli zestaw uprawnień, który zawiera niestandardowe uprawnienie, nie jest już dłużej używany przez zasady. Jednakże, należy usunąć zestaw, który implementuje niestandardowe uprawnienie z listy o pełnym zaufaniu, tylko wtedy, gdy zestaw nie implementuje żadnych innych niestandardowych uprawnień, które nadal są używane. Po usunięciu zestawu z listy, należy także usunąć wszystkie inne zależne zestawy.|  
|**-remgroup** {*etykiety &#124; nazwa*}<br /><br /> lub<br /><br /> **-zarządcy zasobów** {l*abela &#124; nazwa*}|Usuwa grupę kodu określoną za pomocą nazwy lub etykiety. Jeżeli określona grupa kodu posiada podrzędne grupy kodu, Caspol.exe usunie także wszystkie podrzędne grupy kodu.|  
|**-rempset** *nazwa_zestawu_uprawnień*<br /><br /> lub<br /><br /> **-rp** *nazwa_zestawu_uprawnień*|Usuwa określony zestaw uprawnień z zasad. *Nazwa_zestawu_uprawnień* argument wskazuje, które uprawnienia ustawione do usunięcia. Caspol.exe usuwa zestaw uprawnień tylko wtedy, gdy nie jest skojarzony z żadną grupą kodu. Domyślne (wbudowane) zestawy uprawnień nie mogą zostać usunięte.|  
|**-resetowania**<br /><br /> lub<br /><br /> **-r**|Przywraca zasadom domyślny stan i zapisuje je na dysku. Jest to użyteczne, gdy zmienione zasady są nie do naprawienia i trzeba rozpocząć od nowa, z domyślnymi ustawieniami instalacji. Resetowanie może być również wygodne, gdy zachodzi potrzeba użycia domyślnych zasad jako punktu początkowego do modyfikacji określonych plików konfiguracji zabezpieczeń. Aby uzyskać więcej informacji, zobacz [ręczna Edycja plików konfiguracji zabezpieczeń](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> lub<br /><br /> **-rsld**|Zwraca zasady bardziej restrykcyjne wersji stanu domyślnego i utrwala go na dysku; Tworzy kopię zapasową poprzednich zasad komputera i utrwala go w pliku o nazwie `security.config.bac`.  Zasad zablokowane w dół przypomina domyślne zasady z tą różnicą, że zasada nie udziela żadnych uprawnień do kodu z `Local Intranet`, `Trusted Sites`, i `Internet` stref i odpowiednie grupy kodów zostały żadne grupy kod podrzędny.|  
|**-resolvegroup** *assembly_file*<br /><br /> lub<br /><br /> **-rsg***assembly_file* |Grupy kodów wskazuje, że określony zestaw (*assembly_file*) należy do. Domyślnie ta opcja wyświetla poziomy zasad komputera, użytkownika i przedsiębiorstwa, do których należy zestaw. Aby wyświetlić tylko jeden poziom zasad, użyj tej opcji w trybie **-maszyny**, **-użytkownika**, lub **-enterprise** opcji.|  
|**-resolveperm** *assembly_file*<br /><br /> lub<br /><br /> **-źródło** *assembly_file*|Wyświetla wszystkie uprawnienia, które zostaną przydzielone zestawowi, przez określony (lub domyślny) poziom zasad bezpieczeństwa, gdyby zestaw mógł być uruchomiony. *Assembly_file* argument określa zestaw. Jeśli określisz **— wszystkie** opcji Caspol.exe oblicza uprawnienia dla zestawu na podstawie zasad użytkownika, komputera i enterprise; w przeciwnym razie Zastosuj reguły zachowanie domyślne.|  
|**-s**[**esy zabezpieczeń**] {**na** &#124; **poza**}|Włącza lub wyłącza zabezpieczenia dostępu kodu. Określanie **-s poza** opcja nie powoduje wyłączenia zabezpieczeń opartych na rolach. **Uwaga:** tego przełącznika zostanie usunięta w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md). **Uwaga:** wyłączenie zabezpieczeń dostępu kodu, wszystkie żądania dostępu do kodu powiodło się. Wyłączenie zabezpieczeń dostępu kodu sprawia, że system staje się podatny na ataki złośliwego kodu, takiego jak wirusy i robaki. Wyłączenie zabezpieczeń wpływa na zwiększenie wydajności, ale powinno być stosowane tylko wtedy, gdy zastosowano wszelkie inne zabezpieczenia, aby zapewnić, że ogólne zabezpieczenia systemu nie zostały naruszone. Przykłady innych środków ostrożności to: odłączenie od sieci publicznych, fizyczne zabezpieczanie komputerów i tak dalej.|  
|**-u**[**ser**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad użytkownika, w którego imieniu Caspol.exe jest uruchomiony. Użytkownicy niebędący administratorami **-użytkownika** jest ustawieniem domyślnym.|  
|**-?**|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
  
 *Członkostwo* argumentu, który określa warunek członkostwa grupy kodów, może być używany z **- addgroup** i **- chggroup** opcje. Każdy *członkostwo* argument jest zaimplementowany jako klasy .NET Framework. Aby określić *członkostwo,* użyj jednej z następujących czynności.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**-allcode**|Określa cały kod. Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.AllMembershipCondition>.|  
|**-appdir**|Określa katalog aplikacji. Jeśli określisz **— appdir** jako warunek członkostwa dowód adresu URL kodu jest porównywana z świadectwo katalogu aplikacji, kodu. Jeśli obie wartości są takie same, warunek członkostwa jest spełniony. Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition>.|  
|**-niestandardowych***plik_xml* |Dodaje niestandardowy warunek członkostwa. Obowiązkowe *plik_xml* argument określa plik XML, który zawiera serializacja XML warunek członkostwa niestandardowych.|  
|**-hash** *Algorytm_mieszania* {**-szesnastkowych** *hashValue* &#124; **-pliku** *assembly_file* }|Określa kod, który posiada podany skrót zestawu. Aby użyć skrótu jako warunku członkostwa grupy kodu, należy określić wartość skrótu lub plik zestawu. Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.HashMembershipCondition>.|  
|**-pub** { **-cert** *cert_file_name* &#124;<br /><br /> **-plik** *signed_file_name* &#124; **-szesnastkowych***hex_string* }|Określa kod, który posiada podanego wydawcę oprogramowania wskazanego przez plik certyfikatu, sygnaturę pliku lub reprezentację szesnastkową certyfikatu X509. Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.PublisherMembershipCondition>.|  
|**-witryny** *witryny sieci Web*|Określa kod, który posiada określoną witrynę pochodzenia. Na przykład:<br /><br /> **-witryny** www.proseware.com<br /><br /> Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.SiteMembershipCondition>.|  
|**-strong - pliku** *nazwa_pliku* {*nazwa* &#124; **- noname**} {*wersji* &#124; **- noversion**}|Określa kod, który ma określone silnej nazwy jako wyznaczony przez nazwę pliku, nazwa zestawu jako ciąg, a wersja zestawu w formacie *głównych*. *drobne*. *Tworzenie*. *poprawki*. Na przykład:<br /><br /> **-strong - pliku** myAssembly.exe myAssembly 1.2.3.4<br /><br /> Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.StrongNameMembershipCondition>.|  
|**— adres url** *adresu URL*|Określa kod, który pochodzi z określonego adresu URL. Adres URL musi zawierać nazwę protokołu, taką jak http:// lub ftp://. Ponadto symbolu wieloznacznego (\*) może służyć do określenia wielu zestawów z określonego adresu URL. **Uwaga:** ponieważ można ustalić adresu URL za pomocą wielu nazw przy użyciu adresu URL jako warunek członkostwa nie jest bezpiecznym sposobem sprawdzenia tożsamości kodu. Gdy jest to możliwe, należy używać silnej nazwy jako warunku członkostwa, wydawcy jako warunku członkostwa lub skrótu jako warunku członkostwa. <br /><br /> Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.UrlMembershipCondition>.|  
|**-strefy** *nazwa_strefy*|Określa kod, który pochodzi z określonej strefy. *Nazwa_strefy* argument może mieć jedną z następujących wartości: **Mój komputer**, **Intranet**, **zaufane**, **Internet** , lub **niezaufanych**. Aby uzyskać więcej informacji na temat ten warunek członkostwa, zobacz <xref:System.Security.Policy.ZoneMembershipCondition> klasy.|  
  
 *Flagi* argumentu, który może być używany z **— addgroup** i **— chggroup** opcje, jest określany przy użyciu jednej z następujących czynności.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**— Opis "** *opis* **"**|Jeśli jest używana z **— addgroup** opcji, określa opis grupę kodów do dodania. Jeśli jest używana z **— chggroup** opcji, określa opis grupę kodów do edycji. *Opis* argument musi być ujęta w cudzysłów.|  
|**-wyłącznego** {**na**&#124; **Wyłącz**}|Jeśli wartość **na**, wskazuje, że tylko zestaw uprawnień, które są skojarzone z grupą kodu w przypadku dodawania lub modyfikowania jest uznawany za po kodu spełnia warunek członkostwa grupy kodów. Gdy ta opcja jest ustawiona na **poza**, Caspol.exe uwzględnia zestawów uprawnień wszystkie zgodne grupy kodów poziomu zasad.|  
|**-levelfinal** {**on**&#124;**off**}|Jeśli wartość **na**, wskazuje, czy nie poziomu zasad poniżej poziomu, w którym występuje grupy dodane lub zmodyfikowane kodu jest uznawany za. Ta opcja jest typowo używana na poziomie zasad komputera. Na przykład, jeśli flaga grupy kodu ustawiona będzie na poziom komputera i jakiś kod odpowiada warunkowi członkostwa grupy kodu, Caspol.exe nie oblicza ani nie stosuje zasad poziomu użytkownika dla tego kodu.|  
|**-name "** *nazwa* **"**|Jeśli jest używana z **— addgroup** opcji, określa nazwę skryptu dla grupy kod dodać. Jeśli jest używana z **- chggroup** opcji, określa nazwę skryptu dla grupy kod edytować. *Nazwa* argument musi być ujęta w cudzysłów. *Nazwa* argument nie może rozpoczynać się cyfrą i może zawierać tylko A-Z, 0-9 i znaków podkreślenia. Grupy kodów mogą być przywoływane przez to *nazwa* zamiast przez ich etykiet liczbowych. *Nazwa* jest również bardzo przydatne w przypadku skryptów.|  
  
## <a name="remarks"></a>Uwagi  
 Zasady zabezpieczeń są wyrażone za pomocą trzech poziomów zasad: zasady komputera, zasady użytkownika i zasady przedsiębiorstwa. Zestaw uprawnień otrzymanych przez zestaw jest określony przez przecięcie zestawów uprawnień dopuszczonych przez trzy poziomy zasad. Każdy poziom zasad jest reprezentowany przez hierarchiczną strukturę grup kodu. Każda grupa kodu posiada warunek członkostwa, który określa, jaki kod jest członkiem tej grupy. Nazwany zestaw uprawnień jest również skojarzony z każdą grupą kodu. Ten zestaw uprawnień określa uprawnienia, które spełniają warunek członkostwa, jakie środowisko uruchomieniowe przydziela kodowi. Hierarchia grup kodu ze skojarzonymi nazwanymi zestawami uprawnień definiuje i utrzymuje każdy poziom zasad zabezpieczeń. Można użyć**— użytkownik**, **- customuser**, **— maszyny** i **-enterprise** opcje można ustawić poziomu zasad zabezpieczeń.  
  
 Aby uzyskać więcej informacji na temat zasad zabezpieczeń i jak środowisko uruchomieniowe określa uprawnienia, których chcesz udzielić kod, zobacz [Zarządzanie zasadami dotyczącymi zabezpieczeń](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odwoływanie się do grup kodu i zestawów uprawnień  
 Ułatwia odwołania do kodu grup w hierarchii, **-listy** opcja powoduje wyświetlenie wcięta listę grup kodów wraz z ich etykiety wartości liczbowych (1, 1.1, 1.1.1 itd.). Inne operacje wiersza polecenia przeznaczone dla grup kodu także używają etykiet liczbowych, aby odwołać się do określonej grupy kodu.  
  
 Odwołania do nazwanych zestawów uprawnień możliwe są przy użyciu ich nazw. **— Lista** opcja wyświetla listę grup kodów następuje listę uprawnień o nazwie ustawia dostępnych w tych zasadach.  
  
## <a name="caspolexe-behavior"></a>Zachowanie Caspol.exe  
 Wszystkie opcje z wyjątkiem **-s**[**esy zabezpieczeń**] {**na** &#124; **poza**} przy użyciu wersji .NET Framework, która Caspol.exe został zainstalowany z. Jeśli możesz uruchomić Caspol.exe zainstalowanej wersji *X* środowiska uruchomieniowego, zmiany dotyczą tylko do tej wersji. Inne instalacje środowiska uruchomieniowego, jeśli są, nie zostaną uwzględnione. Jeżeli program Caspol.exe jest uruchamiany w wierszu poleceń poza katalogiem określonej wersji środowiska uruchomieniowego, narzędzie jest wykonywane w pierwszym katalogu wersji środowiska uruchomieniowego w ścieżce (zazwyczaj ostatnio zainstalowane środowisko uruchomieniowe).  
  
 **-S**[**esy zabezpieczeń**] {**na** &#124; **poza**} opcji jest operacją całego komputera. Wyłączenie zabezpieczeń dostępu kodu przerywa sprawdzenia zabezpieczeń dla całego kodu zarządzanego i dla wszystkich użytkowników komputera. Jeżeli jest zainstalowanych wiele wersji platformy .NET Framework, to polecenie wyłączy zabezpieczenia dla każdej zainstalowanej wersji na komputerze. Mimo że **— lista** opcja zawiera wyłączenia zabezpieczeń, nic nie else wyraźnie wskazuje dla innych użytkowników, którzy zabezpieczeń została wyłączona.  
  
 Po uruchomieniu Caspol.exe użytkownik bez uprawnień administracyjnych wszystkie opcje dotyczą zasady na poziomie użytkownika, chyba że **— maszyny** określono opcję. Gdy administrator uruchamia Caspol.exe, wszystkie opcje odnoszą się do zasad komputera, chyba że **— użytkownik** określono opcję.  
  
 Caspol.exe musi otrzymać równoważne **wszystko** zestaw uprawnień do funkcji. Narzędzie posiada mechanizm zabezpieczający, który uniemożliwia modyfikowanie zasad w sposób uniemożliwiający udzielenia Caspol.exe uprawnień, których potrzebuje do uruchomienia. Podczas próby zmiany ustawień program Caspol.exe powiadamia, że żądana zmiana zasad spowoduje awarię narzędzia i zmiana zasad zostanie odrzucona. Można wyłączyć ten mechanizm ochrony dla danego polecenia przy użyciu **— wymusić** opcji.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Ręczna edycja plików konfiguracji zabezpieczeń  
 Trzy pliki konfiguracji zabezpieczeń odnoszą się do trzech poziomów zabezpieczeń obsługiwanych przez Caspol.exe: jeden dla zasad komputera, jeden dla podanego użytkownika i jeden dla zasad przedsiębiorstwa. Te trzy pliki są tworzone na dysku tylko wtedy, gdy zasady komputera, użytkownika lub przedsiębiorstwa są zmienione za pomocą Caspol.exe. Można użyć **— Resetuj** w Caspol.exe opcję, aby zapisać domyślnych zasad zabezpieczeń dla dysku, jeśli to konieczne.  
  
 W większości przypadków ręczna edycja plików konfiguracji zabezpieczeń nie jest zalecana. Jednak mogą pojawić się scenariusze, w których modyfikowanie tych plików może być konieczne, na przykład gdy administrator chce edytować konfigurację zabezpieczeń dla określonego użytkownika.  
  
## <a name="examples"></a>Przykłady  
 **-addfulltrust**  
  
 Zakłada, że zestaw uprawnień zawierający niestandardowe uprawnienie został dodany do zasad komputera. To uprawnienie niestandardowy jest zaimplementowana w `MyPerm.exe`, i `MyPerm.exe` odwołuje się do klasy w `MyOther.exe`. Oba zestawy muszą być dodane do listy zestawów o pełnym zaufaniu. Następujące polecenie dodaje `MyPerm.exe` zestawu do listy pełne zaufanie do zasad komputera.  
  
```  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Następujące polecenie dodaje `MyOther.exe` zestawu do listy pełne zaufanie do zasad komputera.  
  
```  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Następujące polecenie dodaje podrzędną grupę kodu do korzenia hierarchii grup kodu zasad komputera. Nową grupę kodu jest elementem członkowskim **Internet** strefy i jest skojarzony z **wykonywania** zestaw uprawnień.  
  
```  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Następujące polecenie dodaje grupę kodów podrzędnych, zapewniająca udział \\\netserver\netshare uprawnienia lokalny intranet.  
  
```  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Następujące polecenie dodaje `Mypset` uprawnienia do zasad użytkownika.  
  
```  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Następujące zmiany polecenie zestaw uprawnień na zasady użytkownika grupy kodów etykietami 1.2. Aby **wykonywania** zestaw uprawnień.  
  
```  
caspol -user -chggroup 1.2. Execution  
```  
  
 Następujące zmiany polecenia 1.2.1 oznaczony jako warunek członkostwa w domyślnych zasad grupy kodów. i zmienia ustawienie **wyłącznego** flagi. Warunek członkostwa jest zdefiniowane jako kod, który pochodzi z **Internet** strefy i **wyłącznego** flaga jest włączona.  
  
```  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Następujące polecenie zmienia zestawu o nazwie uprawnień `Mypset` do zestawu zawarte w uprawnień `newpset.xml`. Należy zauważyć, że aktualne wydanie nie obsługuje zmiany zestawów uprawnień, które są używane przez hierarchię grup kodu.  
  
```  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 Poniższe polecenie powoduje, że zasady użytkownika głównej grupy kodów (etykietą 1) ma zostać skojarzony z **nic** nazwany zestaw uprawnień. Uniemożliwia to uruchomienie programu Caspol.exe.  
  
```  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-odzyskiwanie**  
  
 Następujące polecenie odzyskuje ostatnie zapisane zasady komputera.  
  
```  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 Następujące polecenie usuwa grupę kodu z etykietą 1.1. Jeśli grupa kodu posiada węzły podrzędne, te grupy również zostaną usunięte.  
  
```  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 Następujące polecenie usuwa **wykonywania** uprawnienia z zasad użytkownika.  
  
```  
caspol -user -rempset Execution  
```  
  
 Następujące polecenie usuwa `Mypset` z poziomu zasad użytkownika.  
  
```  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Polecenie wyświetla kod grupy zasad komputera `myassembly` należy.  
  
```  
caspol -machine -resolvegroup myassembly  
```  
  
 Polecenie zawiera wszystkich grup kodów maszyny, enterprise i określony użytkownik niestandardowych zasad `myassembly` należy.  
  
```  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Polecenie oblicza uprawnienia dla `testassembly` oparte na poziomy zasad komputera i użytkownika.  
  
```  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
