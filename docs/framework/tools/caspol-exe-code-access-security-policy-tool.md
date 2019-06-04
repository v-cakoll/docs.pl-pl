---
title: Caspol.exe (Narzędzie zasad zabezpieczeń dostępu kodu)
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccb1d78f939d2faf90013392fc60d5597bc3922e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489675"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Narzędzie zasad zabezpieczeń dostępu kodu)
Narzędzie (Caspol.exe) sprawdzania zabezpieczeń dostępu kodu (CAS) pozwala użytkownikom i administratorom na modyfikowanie zasad bezpieczeństwa na poziomie zasad komputera, na poziomie zasad użytkownika i na poziomie zasad przedsiębiorstwa.  
  
> [!IMPORTANT]
>  Począwszy od programu .NET Framework 4, Caspol.exe nie wpływa na zasady CAS chyba że [ \<legacyCasPolicy > element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ustawiono `true`. Wszelkie ustawienia pokazywane lub modyfikowane przez narzędzie CasPol.exe wpływają tylko na aplikacje, w których są stosowane zasady CAS. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
> [!NOTE]
>  Na komputerach 64-bitowych dostępne są obie, 32-bitowa i 64-bitowa, wersje zasad zabezpieczeń. Aby upewnić się, że zmiany zasad mają zastosowanie do obu, 32-bitowych i 64-bitowych aplikacji, należy uruchomić obie, 32-bitową i 64-bitową, wersję Caspol.exe.  
  
 Narzędzie sprawdzania zabezpieczeń dostępu kodu jest automatycznie instalowane z .NET Framework i z programem Visual Studio. Możesz znaleźć Caspol.exe w %windir%\Microsoft.NET\Framework\\*wersji* w systemach 32-bitowych lub %windir%\Microsoft.NET\Framework64\\*wersji* w systemach 64-bitowych. (Na przykład lokalizacja to %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe dla .NET Framework 4 w systemach 64-bitowych). Może być zainstalowanych wiele wersji narzędzia, jeżeli komputer używa równolegle wielu wersji platformy .NET Framework. Narzędzie można uruchomić z katalogu instalacji. Jednak firma Microsoft zaleca użycie [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md), co nie wymaga przechodzenia do folderu instalacji.  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
caspol [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-af** *assembly_file*|Dodaje zestaw, który implementuje niestandardowy obiekt zabezpieczeń (taki jak niestandardowe uprawnienia lub niestandardowe warunki członkostwa), do listy zestawów o pełnym zaufaniu dla specyficznego poziomu zasad. *Assembly_file* argument określa zestaw do dodania. Ten plik musi być podpisany przy użyciu [silnej nazwy](../../../docs/framework/app-domains/strong-named-assemblies.md). Możesz zarejestrować zestaw z silną nazwą przy użyciu [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).<br /><br /> Za każdym razem, gdy zestaw uprawnień zawierający niestandardowe uprawnienia jest dodawany do zasad, zestaw implementujący niestandardowe uprawnienia musi zostać dodany do listy zestawów o pełnym zaufaniu dla danego poziomu zasad. Zestawy, które implementują niestandardowe obiekty zabezpieczeń (takie jak niestandardowe grupy kodu lub warunki członkostwa) używane w zasadach zabezpieczeń (takich jak zasady komputera) powinny być zawsze dodawane do listy zestawów pełnego zaufania. **Uwaga:**  Jeśli zestaw implementujący niestandardowe obiekty zabezpieczeń odwołuje się do innych zestawów, należy najpierw dodać do listy zestawów o pełnym zaufaniu zestawy, do których ma miejsce odwołanie. Niestandardowe obiekty zabezpieczeń stworzone za pomocą języków Visual Basic, C++ i JScript odwołują się odpowiednio do Microsoft.VisualBasic.dll, Microsoft.VisualC.dll lub Microsoft.JScript.dll. Zestawy te nie znajdują się domyślnie na liście zestawów o pełnym zaufaniu. Należy dodać odpowiedni zestaw do listy o pełnym zaufaniu przed dodaniem niestandardowego obiektu zabezpieczeń. Niewykonanie tej czynności spowoduje awarię systemu zabezpieczeń, powodując niepowodzenie ładowania zestawów. W takiej sytuacji programu Caspol.exe **-all - resetowania** opcji nie naprawi zabezpieczeń. W celu naprawienia zabezpieczeń należy ręcznie wyedytować pliki zabezpieczeń, aby usunąć niestandardowy obiekt zabezpieczeń.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*flags*]<br /><br /> lub<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*flags*]|Dodaje nową grupę kodu do hierarchii grup kodu. Można określić *parent_label* lub *parent_name*. *Parent_label* argument Określa etykietę (taką jak 1. lub 1.1.) grupy kodu, który jest elementem nadrzędnym dodawanej grupy kodu. *Parent_name* argument określa nazwę grupy kodu, który jest elementem nadrzędnym dodawanej grupy kodu. Ponieważ *parent_label* i *parent_name* mogą być używane zamiennie, Caspol.exe musi mieć możliwość rozróżnienia między nimi. W związku z tym *parent_name* nie może zaczynać się liczbą. Ponadto *parent_name* może zawierać tylko A-Z, 0-9 i znak podkreślenia.<br /><br /> *Mship* argument określa warunek członkostwa dla nowej grupy kodu. Aby uzyskać więcej informacji, zobacz tabelę *mship* argumentów w dalszej części tej sekcji.<br /><br /> *Pset_name* argument jest nazwą zestawu uprawnień, które mają zostać skojarzone z nową grupą kodu. Można również ustawić co najmniej jeden *flagi* dla nowej grupy. Aby uzyskać więcej informacji, zobacz tabelę *flagi* argumentów w dalszej części tej sekcji.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> lub<br /><br /> **-ap** {*named*_*psfile* &#124; *psfile* *pset_name*}|Dodaje nowy, nazwany zestaw uprawnień do zasad. Zestaw uprawnień musi być w formacie XML i być zapisany w pliku xml. Jeśli plik XML zawiera nazwę uprawnienia, tylko tego pliku zestawu (*psfile*) jest określony. Jeśli plik XML nie zawiera nazwy zestawu uprawnień, należy określić zarówno nazwę pliku XML (*psfile*) i nazwę zestawu uprawnień (*pset_name*).<br /><br /> Należy zauważyć, że wszystkie uprawnienia użyte w zestawie uprawnień muszą być zdefiniowane w zestawie zawartym w globalnej pamięci podręcznej zestawów.|  
|**-a**[**ll**]|Wskazuje, że wszystkie opcje następujące po niej mają zastosowanie do zasad komputera, użytkownika i przedsiębiorstwa. **— Wszystkie** opcja zawsze odwołuje się do zasad aktualnie zalogowanego użytkownika. Zobacz **- customall** opcję, aby odwoływać się do zasad użytkownika innego niż bieżący użytkownik.|  
|**-chggroup** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flagi* `}`<br /><br /> lub<br /><br /> **-cg** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flagi* `}`|Zmienia warunek członkostwa grupy kodu, zestaw uprawnień lub ustawień **wyłączne**, **levelfinal**, **nazwa**, lub **opis**flagi. Można określić *etykiety* lub *nazwa*. *Etykiety* argument Określa etykietę (taką jak 1. lub 1.1.) grupy kodu. *Nazwa* argument określa nazwę grupy kodu do zmiany. Ponieważ *etykiety* i *nazwa* mogą być używane zamiennie, Caspol.exe musi mieć możliwość rozróżnienia między nimi. W związku z tym *nazwa* nie może zaczynać się liczbą. Ponadto *nazwa* może zawierać tylko A-Z, 0-9 i znak podkreślenia.<br /><br /> *Pset_name* argument określa nazwę zestaw uprawnień, aby skojarzyć z grupą kodu. Zobacz tabele w dalszej części tej sekcji, aby uzyskać informacje na *mship* i *flagi* argumentów.|  
|**-chgpset** *psfile pset_name*<br /><br /> lub<br /><br /> **-cp** *psfile pset_name*|Zmienia nazwany zestaw uprawnień. *Psfile* argument dostarcza nową definicję zestawu uprawnień; jest to Zserializowany plik zestawu uprawnień w formacie XML. *Pset_name* argument określa nazwę zestawu uprawnień, które chcesz zmienić.|  
|**-customall** *ścieżki*<br /><br /> lub<br /><br /> **-ca** *ścieżki*|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do zasad komputera, przedsiębiorstwa i określonych niestandardowych zasad użytkownika. Należy określić lokalizację pliku konfiguracji zabezpieczeń użytkownika niestandardowego z *ścieżki* argumentu.|  
|**-cu**[**stomuser**] *path*|Umożliwia administrację niestandardowymi zasadami użytkownika, które nie należą do użytkownika, w którego imieniu program Caspol.exe jest aktualnie uruchomiony. Należy określić lokalizację pliku konfiguracji zabezpieczeń użytkownika niestandardowego z *ścieżki* argumentu.|  
|**-enterprise**<br /><br /> lub<br /><br /> **-pl**|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad przedsiębiorstwa. Użytkownicy, którzy nie są administratorami przedsiębiorstwa, nie posiadają wystarczających praw, aby modyfikować zasady przedsiębiorstwa, jednak mogą je wyświetlać. W scenariuszach bez przedsiębiorstwa zasady te domyślnie nie kolidują z zasadami komputera i użytkownika.|  
|**-e**[**xecution**] {**na** &#124; **poza**}|Włącza lub wyłącza mechanizm sprawdzający uprawnienia uruchamiania przed rozpoczęciem wykonywania kodu. **Uwaga:**  Ten przełącznik został usunięty w .NET Framework 4 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).|  
|**-f**[**orce**]|Pomija test samolikwidacji narzędzia i zmienia zasady określone przez użytkownika. Normalnie Caspol.exe sprawdza, czy dowolne zmiany zasad mogą uniemożliwić programowi Caspol.exe poprawne działanie; jeśli tak, Caspol.exe nie zapisze zmian zasad i wyświetli komunikat o błędzie. Aby wymusić Caspol.exe zmianę zasad, nawet jeśli to uniemożliwia Caspol.exe uruchomiona, należy użyć **— wymusić** opcji.|  
|**-h**[**elp**]|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
|**-l**[**ist**]|Wypisuje hierarchię grup kodu i zestawy uprawnień dla określonego komputera, użytkownika, przedsiębiorstwa lub wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listdescription**<br /><br /> lub<br /><br /> **-ld**|Wypisuje opisy wszystkich grup kodu dla określonego poziomu zasad.|  
|**-listfulltrust**<br /><br /> lub<br /><br /> **-lf**|Wypisuje zawartość listy zestawów o pełnym zaufaniu dla określonego poziomu zasad.|  
|**-listgroups**<br /><br /> lub<br /><br /> **-lg**|Wypisuje grupy kodu dla określonego poziomu zasad lud dla wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listpset** lub **-lp**|Wyświetla zestawy uprawnień dla określonego poziomu zasad lub poziomów zasad.|  
|**-m**[**achine**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad komputera. Użytkownicy, którzy nie są administratorami, nie posiadają wystarczających praw, aby modyfikować zasady komputera, jednak mogą je wyświetlać. Dla administratorów **-machine** jest ustawieniem domyślnym.|  
|**-polchgprompt** {**on** &#124; **off**}<br /><br /> lub<br /><br /> **-pp** {**na** &#124; **poza**}|Włącza lub wyłącza monit, który jest wyświetlany zawsze, gdy Caspol.exe jest uruchamiany z opcją powodującą zmianę zasad.|  
|**-quiet**<br /><br /> lub<br /><br /> **-q**|Tymczasowo wyłącza monit, który jest normalnie wyświetlany dla opcji powodującej zmianę zasad. Globalne ustawienie monitu nie jest zmieniane. Należy użyć tej opcji w pojedynczym poleceniu, aby uniknąć wyłączenia monitu dla wszystkich poleceń Caspol.exe.|  
|**-r**[**ecover**]|Odzyskuje zasady z pliku kopii zapasowej. Zawsze, gdy zmieniane są zasady, Caspol.exe zapisuje stare zasady w pliku kopii zapasowej.|  
|**-remfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-rf** *assembly_file*|Usuwa zestaw z listy zestawów o pełnym zaufaniu poziomu zasad. Ta operacja powinna być wykonana, jeśli zestaw uprawnień, który zawiera niestandardowe uprawnienie, nie jest już dłużej używany przez zasady. Jednakże, należy usunąć zestaw, który implementuje niestandardowe uprawnienie z listy o pełnym zaufaniu, tylko wtedy, gdy zestaw nie implementuje żadnych innych niestandardowych uprawnień, które nadal są używane. Po usunięciu zestawu z listy, należy także usunąć wszystkie inne zależne zestawy.|  
|**-remgroup** {*label &#124;name*}<br /><br /> lub<br /><br /> **-rg** {l*abel &#124; nazwa*}|Usuwa grupę kodu określoną za pomocą nazwy lub etykiety. Jeżeli określona grupa kodu posiada podrzędne grupy kodu, Caspol.exe usunie także wszystkie podrzędne grupy kodu.|  
|**-rempset** *pset_name*<br /><br /> lub<br /><br /> **-rp** *pset_name*|Usuwa określony zestaw uprawnień z zasad. *Pset_name* argument wskazuje, który zestaw uprawnień do usunięcia. Caspol.exe usuwa zestaw uprawnień tylko wtedy, gdy nie jest skojarzony z żadną grupą kodu. Domyślne (wbudowane) zestawy uprawnień nie mogą zostać usunięte.|  
|**-resetowania**<br /><br /> lub<br /><br /> **-r**|Przywraca zasadom domyślny stan i zapisuje je na dysku. Jest to użyteczne, gdy zmienione zasady są nie do naprawienia i trzeba rozpocząć od nowa, z domyślnymi ustawieniami instalacji. Resetowanie może być również wygodne, gdy zachodzi potrzeba użycia domyślnych zasad jako punktu początkowego do modyfikacji określonych plików konfiguracji zabezpieczeń. Aby uzyskać więcej informacji, zobacz [ręczna Edycja plików konfiguracji zabezpieczeń](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> lub<br /><br /> **-rsld**|Przywraca zasadom bardziej restrykcyjną wersję stanu domyślnego i zapisuje je na dysku Tworzy kopię zapasową poprzednich zasad komputera i zapisuje je w pliku o nazwie `security.config.bac`.  Zablokowane zasady są podobne do zasad domyślnych, z tą różnicą, że zasady nie udzielają uprawnień do kodu z `Local Intranet`, `Trusted Sites`, i `Internet` stref i odpowiadających im grup kodu mają nie podrzędne grupy kodu.|  
|**-resolvegroup** *assembly_file*<br /><br /> lub<br /><br /> **-rsg**  *assembly_file*|Wyświetla grupy kodu, w których należy określony zestaw (*assembly_file*) należy do. Domyślnie ta opcja wyświetla poziomy zasad komputera, użytkownika i przedsiębiorstwa, do których należy zestaw. Aby wyświetlić tylko jeden poziom zasad, użyj tej opcji z oboma **-maszyny**, **-użytkownika**, lub **— enterprise** opcji.|  
|**-resolveperm** *assembly_file*<br /><br /> lub<br /><br /> **-rsp** *assembly_file*|Wyświetla wszystkie uprawnienia, które zostaną przydzielone zestawowi, przez określony (lub domyślny) poziom zasad bezpieczeństwa, gdyby zestaw mógł być uruchomiony. *Assembly_file* argument określa zestaw. Jeśli określisz **— wszystkie** opcja, Caspol.exe obliczy uprawnienia dla zestawu, na podstawie zasad użytkownika, komputera i przedsiębiorstwa; w przeciwnym razie zastosować domyślne reguły zachowania.|  
|**-s**[**ecurity**] {**na** &#124; **poza**}|Włącza lub wyłącza zabezpieczenia dostępu kodu. Określanie **-s off** opcji nie wyłącza zabezpieczeń opartych na rolach. **Uwaga:**  Ten przełącznik został usunięty w .NET Framework 4 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md). **Uwaga:**  Gdy zabezpieczenia dostępu kodu są wyłączone, wszystkie żądania dostępu do kodu kończą się powodzeniem. Wyłączenie zabezpieczeń dostępu kodu sprawia, że system staje się podatny na ataki złośliwego kodu, takiego jak wirusy i robaki. Wyłączenie zabezpieczeń wpływa na zwiększenie wydajności, ale powinno być stosowane tylko wtedy, gdy zastosowano wszelkie inne zabezpieczenia, aby zapewnić, że ogólne zabezpieczenia systemu nie zostały naruszone. Przykłady innych środków ostrożności to: odłączenie od sieci publicznych, fizyczne zabezpieczanie komputerów i tak dalej.|  
|**-u**[**ser**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad użytkownika, w którego imieniu Caspol.exe jest uruchomiony. Dla użytkowników niebędących administratorami opcja **— użytkownik** jest ustawieniem domyślnym.|  
|**-?**|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
  
 *Mship* argumentu, który określa warunek członkostwa grupy kodu, może być używany z **- addgroup** i **- chggroup** opcje. Każdy *mship* argument jest implementowany jako klasa .NET Framework. Aby określić *mship* użyj jednej z następujących czynności.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**-allcode**|Określa cały kod. Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>.|  
|**-appdir**|Określa katalog aplikacji. Jeśli określisz **– appdir** jako warunku członkostwa, dowód URL kodu jest porównywany z dowodem katalogu aplikacji danego kodu. Jeśli obie wartości są takie same, warunek członkostwa jest spełniony. Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>.|  
|**-niestandardowe** *xmlfile*|Dodaje niestandardowy warunek członkostwa. Obowiązkowy *xmlfile* argument określa plik XML, który zawiera serializacji XML niestandardowy warunek członkostwa.|  
|**-hash** *hashAlg* { **-hex** *hashValue* &#124; **-file** *assembly_file* }|Określa kod, który posiada podany skrót zestawu. Aby użyć skrótu jako warunku członkostwa grupy kodu, należy określić wartość skrótu lub plik zestawu. Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>.|  
|**-pub** { **-cert** *cert_file_name* &#124;<br /><br /> **-file** *signed_file_name* &#124; **-hex**  *hex_string* }|Określa kod, który posiada podanego wydawcę oprogramowania wskazanego przez plik certyfikatu, sygnaturę pliku lub reprezentację szesnastkową certyfikatu X509. Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>.|  
|**-witryny** *witryny sieci Web*|Określa kod, który posiada określoną witrynę pochodzenia. Na przykład:<br /><br /> `-site** www.proseware.com`<br /><br /> Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>.|  
|**-strong - pliku** *nazwa_pliku* {*nazwa* &#124; **- noname**} {*wersji* &#124; **- noversion**}|Określa kod, który posiada określoną silną nazwę wskazaną przez nazwę pliku, nazwę zestawu jako ciąg i wersję zestawu w formacie *głównych*. *drobne*. *Tworzenie*. *poprawka*. Na przykład:<br /><br /> **-strong - pliku** } myAssembly.exe myAssembly 1.2.3.4<br /><br /> Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>.|  
|**— adres url** *adresu URL*|Określa kod, który pochodzi z określonego adresu URL. Adres URL musi zawierać nazwę protokołu, taką jak `http://` lub `ftp://`. Ponadto symbolu wieloznacznego (\*) można określić wiele zestawów z określonego adresu URL. **Uwaga:**  Ponieważ adres URL może być zidentyfikowany za pomocą wielu nazw, używanie adresu URL, jako warunku członkostwa, nie jest bezpieczną metodą ustalania tożsamości kodu. Gdy jest to możliwe, należy używać silnej nazwy jako warunku członkostwa, wydawcy jako warunku członkostwa lub skrótu jako warunku członkostwa. <br /><br /> Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>.|  
|**-strefy** *zonename*|Określa kod, który pochodzi z określonej strefy. *Zonename* argument może być jednym z następujących wartości: **Mój komputer**, **Intranet**, **zaufanych**, **Internet**, lub **niezaufanych**. Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.ZoneMembershipCondition> klasy.|  
  
 *Flagi* argumentu, który może być używany z **– addgroup** i **– chggroup** opcje, jest określony, przy użyciu jednej z następujących czynności.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**— Opis** "*opis*"|Jeśli używane **– addgroup** opcją, określa opis grupy kodu do dodania. Jeśli używane **– chggroup** opcją, określa opis grupy kodu do edycji. *Opis* argument musi być ujęta w cudzysłów.|  
|**-exclusive** {**on**&#124;**off**}|Po ustawieniu **na**, wskazuje, że tylko zestaw uprawnień skojarzony z grupą kodu w przypadku dodawania lub modyfikowania jest uznawany za gdy jakiś kod spełnia warunek członkostwa grupy kodu. Jeśli ta opcja jest ustawiona **poza**, Caspol.exe uwzględnia zestawy uprawnień wszystkich zgodnych grup kodu na poziomie zasad.|  
|**-levelfinal** {**on**&#124;**off**}|Po ustawieniu **na**, wskazuje, że żaden poziom zasad poniżej poziomu, w której występuje grupy dodane lub zmodyfikowane kodu jest uważana za. Ta opcja jest typowo używana na poziomie zasad komputera. Na przykład, jeśli flaga grupy kodu ustawiona będzie na poziom komputera i jakiś kod odpowiada warunkowi członkostwa grupy kodu, Caspol.exe nie oblicza ani nie stosuje zasad poziomu użytkownika dla tego kodu.|  
|**— Nazwa** "*nazwa*"|Jeśli używane **– addgroup** opcją, określa nazwę skryptową grupy kodu do dodania. Jeśli używane **- chggroup** opcją, określa nazwę skryptową grupy kodu do edycji. *Nazwa* argument musi być ujęta w cudzysłów. *Nazwa* argument nie może zaczynać się liczbą i może zawierać tylko A-Z, 0-9 i znak podkreślenia. Grup kodu mogą być przywoływane przez to *nazwa* zamiast ich etykiet liczbowych. *Nazwa* jest również bardzo przydatna w zastosowaniach skryptowych.|  
  
## <a name="remarks"></a>Uwagi  
 Zasady zabezpieczeń są wyrażone za pomocą trzech poziomów zasad: zasady komputera, zasady użytkownika i zasady przedsiębiorstwa. Zestaw uprawnień otrzymanych przez zestaw jest określony przez przecięcie zestawów uprawnień dopuszczonych przez trzy poziomy zasad. Każdy poziom zasad jest reprezentowany przez hierarchiczną strukturę grup kodu. Każda grupa kodu posiada warunek członkostwa, który określa, jaki kod jest członkiem tej grupy. Nazwany zestaw uprawnień jest również skojarzony z każdą grupą kodu. Ten zestaw uprawnień określa uprawnienia, które spełniają warunek członkostwa, jakie środowisko uruchomieniowe przydziela kodowi. Hierarchia grup kodu ze skojarzonymi nazwanymi zestawami uprawnień definiuje i utrzymuje każdy poziom zasad zabezpieczeń. Możesz użyć **— użytkownik**, **- customuser**, **— maszyny** i **— enterprise** opcje, aby ustawić poziom zasad zabezpieczeń.  
  
 Aby uzyskać więcej informacji na temat zasad zabezpieczeń i jak środowisko uruchomieniowe określa jakie uprawnienia nadać kodowi, zobacz [Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odwoływanie się do grup kodu i zestawów uprawnień  
 Aby ułatwić odwołania do grup kodu w hierarchii, **— lista** opcji Wyświetla listę grup kodu wraz z ich etykietami numerycznymi (1, 1.1, 1.1.1 i tak dalej). Inne operacje wiersza polecenia przeznaczone dla grup kodu także używają etykiet liczbowych, aby odwołać się do określonej grupy kodu.  
  
 Odwołania do nazwanych zestawów uprawnień możliwe są przy użyciu ich nazw. **— Lista** opcji Wyświetla listę grup kodu, a następnie listę nazwanych uprawnień zestawów dostępnych w tych zasadach.  
  
## <a name="caspolexe-behavior"></a>Zachowanie Caspol.exe  
 Wszystkie opcje z wyjątkiem **-s**[**ecurity**] {**na** &#124; **poza**} używana wersja programu .NET Framework, Caspol.exe został zainstalowany za pomocą. Jeżeli program Caspol.exe, który został zainstalowany z wersją *X* środowiska uruchomieniowego, zmiany dotyczą tylko tej wersji. Inne instalacje środowiska uruchomieniowego, jeśli są, nie zostaną uwzględnione. Jeżeli program Caspol.exe jest uruchamiany w wierszu poleceń poza katalogiem określonej wersji środowiska uruchomieniowego, narzędzie jest wykonywane w pierwszym katalogu wersji środowiska uruchomieniowego w ścieżce (zazwyczaj ostatnio zainstalowane środowisko uruchomieniowe).  
  
 **-S**[**ecurity**] {**na** &#124; **poza**} opcji jest operacją całego komputera. Wyłączenie zabezpieczeń dostępu kodu przerywa sprawdzenia zabezpieczeń dla całego kodu zarządzanego i dla wszystkich użytkowników komputera. Jeżeli jest zainstalowanych wiele wersji platformy .NET Framework, to polecenie wyłączy zabezpieczenia dla każdej zainstalowanej wersji na komputerze. Mimo że **— lista** opcja wskazuje, że zabezpieczenia są wyłączone, nic innego jasno nie wskazuje dla innych użytkowników, którzy zabezpieczeń zostało wyłączone.  
  
 Gdy użytkownik bez praw administratora uruchamia Caspol.exe, wszystkie opcje odnoszą się do poziomu zasad użytkownika, chyba że **— machine** określono opcję. Gdy administrator uruchamia Caspol.exe, wszystkie opcje odnoszą się do zasad komputera, chyba że **— użytkownik** określono opcję.  
  
 Caspol.exe musi mieć przyznane odpowiednik **wszystko** zestaw uprawnień do funkcji. Narzędzie posiada mechanizm zabezpieczający, który uniemożliwia modyfikowanie zasad w sposób uniemożliwiający udzielenia Caspol.exe uprawnień, których potrzebuje do uruchomienia. Podczas próby zmiany ustawień program Caspol.exe powiadamia, że żądana zmiana zasad spowoduje awarię narzędzia i zmiana zasad zostanie odrzucona. Możesz wyłączyć ten mechanizm dla podanego polecenia przy użyciu **— wymusić** opcji.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Ręczna edycja plików konfiguracji zabezpieczeń  
 Trzy pliki konfiguracji zabezpieczeń odnoszą się do trzech poziomów zabezpieczeń obsługiwanych przez Caspol.exe: jeden dla zasad komputera, jeden dla podanego użytkownika i jeden dla zasad przedsiębiorstwa. Te trzy pliki są tworzone na dysku tylko wtedy, gdy zasady komputera, użytkownika lub przedsiębiorstwa są zmienione za pomocą Caspol.exe. Możesz użyć **— Resetuj** opcji w Caspol.exe, aby zapisać domyślne zasady zabezpieczeń na dysku, jeśli to konieczne.  
  
 W większości przypadków ręczna edycja plików konfiguracji zabezpieczeń nie jest zalecana. Jednak mogą pojawić się scenariusze, w których modyfikowanie tych plików może być konieczne, na przykład gdy administrator chce edytować konfigurację zabezpieczeń dla określonego użytkownika.  
  
## <a name="examples"></a>Przykłady  
 **-addfulltrust**  
  
 Zakłada, że zestaw uprawnień zawierający niestandardowe uprawnienie został dodany do zasad komputera. Niestandardowe uprawnienie jest zaimplementowane w `MyPerm.exe`, i `MyPerm.exe` odwołuje się do klas w `MyOther.exe`. Oba zestawy muszą być dodane do listy zestawów o pełnym zaufaniu. Następujące polecenie dodaje `MyPerm.exe` zestawu do listy o pełnym zaufaniu dla zasad komputera.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Następujące polecenie dodaje `MyOther.exe` zestawu do listy o pełnym zaufaniu dla zasad komputera.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Następujące polecenie dodaje podrzędną grupę kodu do korzenia hierarchii grup kodu zasad komputera. Nowa grupa kodu jest członkiem **Internet** strefy i jest skojarzona z **wykonywania** zestaw uprawnień.  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Następujące polecenie dodaje podrzędna grupę kodu, który zapewnia udziału \\\netserver\netshare lokalny intranet uprawnień.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Następujące polecenie dodaje `Mypset` zestaw uprawnień, aby zasady użytkownika.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Następujące polecenie zmienia zestaw uprawnień w zasadach użytkownika grupy kodu o etykiecie 1.2. Aby **wykonywania** zestaw uprawnień.  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Następujące polecenie zmienia warunek członkostwa w domyślnych zasadach grupy kodu o etykiecie 1.2.1. i zmienia ustawienie **wyłączne** flagi. Warunek członkostwa jest zdefiniowany jako kod pochodzący ze **Internet** strefy i **wyłączne** flaga jest włączona.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Następujące polecenie zmienia zestaw uprawnień o nazwie `Mypset` na zestaw uprawnień zawarty w `newpset.xml`. Należy zauważyć, że aktualne wydanie nie obsługuje zmiany zestawów uprawnień, które są używane przez hierarchię grup kodu.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 Następujące polecenie powoduje, że zasad użytkownika korzenia grupy kodu (Etykieta 1) ma zostać skojarzony z **nic** nazwany zestaw uprawnień. Uniemożliwia to uruchomienie programu Caspol.exe.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-recover**  
  
 Następujące polecenie odzyskuje ostatnie zapisane zasady komputera.  
  
```console  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 Następujące polecenie usuwa grupę kodu z etykietą 1.1. Jeśli grupa kodu posiada węzły podrzędne, te grupy również zostaną usunięte.  
  
```console  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 Następujące polecenie usuwa **wykonywania** zestaw uprawnień z zasad użytkownika.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Następujące polecenie usuwa `Mypset` z poziomu zasad użytkownika.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Następujące polecenie wyświetla wszystkie grupy kodu zasad komputera, których `myassembly` należy.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Następujące polecenie wyświetla wszystkie grupy kodu komputera, przedsiębiorstwa i niestandardowe zasady określonego użytkownika, których `myassembly` należy.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Następujące polecenie oblicza uprawnienia dla `testassembly` na podstawie poziomów zasad komputera i użytkownika.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
