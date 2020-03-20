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
ms.openlocfilehash: 792d89351b3759984b085fd8aee9c3ae8e012c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180416"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Narzędzie zasad zabezpieczeń dostępu kodu)
Narzędzie (Caspol.exe) sprawdzania zabezpieczeń dostępu kodu (CAS) pozwala użytkownikom i administratorom na modyfikowanie zasad bezpieczeństwa na poziomie zasad komputera, na poziomie zasad użytkownika i na poziomie zasad przedsiębiorstwa.  
  
> [!IMPORTANT]
> Począwszy od programu .NET Framework 4, program Caspol.exe nie wpływa na zasady CAS, chyba że [ \<element> legacyCasPolicy](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) jest ustawiony na `true`. Wszelkie ustawienia pokazywane lub modyfikowane przez narzędzie CasPol.exe wpływają tylko na aplikacje, w których są stosowane zasady CAS. Aby uzyskać więcej informacji, zobacz [Zmiany zabezpieczeń](../security/security-changes.md).  
  
> [!NOTE]
> Na komputerach 64-bitowych dostępne są obie, 32-bitowa i 64-bitowa, wersje zasad zabezpieczeń. Aby upewnić się, że zmiany zasad mają zastosowanie do obu, 32-bitowych i 64-bitowych aplikacji, należy uruchomić obie, 32-bitową i 64-bitową, wersję Caspol.exe.  
  
 Narzędzie sprawdzania zabezpieczeń dostępu kodu jest automatycznie instalowane z .NET Framework i z programem Visual Studio. Program Caspol.exe można znaleźć w\\*wersji* %windir%\Microsoft.NET\Framework w systemach 32-bitowych lub\\%windir%\Microsoft.NET\Framework64*version* w systemach 64-bitowych. (Na przykład lokalizacja to %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe dla programu .NET Framework 4 w systemie 64-bitowym). Wiele wersji narzędzia może być zainstalowanych, jeśli na komputerze jest uruchomionych wiele wersji programu .NET Framework obok siebie. Narzędzie można uruchomić z katalogu instalacji. Zaleca się jednak użycie [wierszy polecenia,](developer-command-prompt-for-vs.md)które nie wymagają przechodzenia do folderu instalacyjnego.  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console
caspol [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-af** *assembly_file*|Dodaje zestaw, który implementuje niestandardowy obiekt zabezpieczeń (taki jak niestandardowe uprawnienia lub niestandardowe warunki członkostwa), do listy zestawów o pełnym zaufaniu dla specyficznego poziomu zasad. *Argument assembly_file* określa zestaw do dodania. Ten plik musi być podpisany przy silnym [nazwisku](../../standard/assembly/strong-named.md). Można podpisać zestaw o silnej nazwie za pomocą [narzędzia Silnej nazwy (Sn.exe).](sn-exe-strong-name-tool.md)<br /><br /> Za każdym razem, gdy zestaw uprawnień zawierający niestandardowe uprawnienia jest dodawany do zasad, zestaw implementujący niestandardowe uprawnienia musi zostać dodany do listy zestawów o pełnym zaufaniu dla danego poziomu zasad. Zestawy, które implementują niestandardowe obiekty zabezpieczeń (takie jak niestandardowe grupy kodu lub warunki członkostwa) używane w zasadach zabezpieczeń (takich jak zasady komputera) powinny być zawsze dodawane do listy zestawów pełnego zaufania. **Uwaga:**  Jeśli zestaw implementujący niestandardowy obiekt zabezpieczeń odwołuje się do innych zestawów, należy najpierw dodać zestawy, do których istnieją odwołania, do listy zestawu pełnego zaufania. Niestandardowe obiekty zabezpieczeń stworzone za pomocą języków Visual Basic, C++ i JScript odwołują się odpowiednio do Microsoft.VisualBasic.dll, Microsoft.VisualC.dll lub Microsoft.JScript.dll. Zestawy te nie znajdują się domyślnie na liście zestawów o pełnym zaufaniu. Należy dodać odpowiedni zestaw do listy o pełnym zaufaniu przed dodaniem niestandardowego obiektu zabezpieczeń. Niewykonanie tej czynności spowoduje awarię systemu zabezpieczeń, powodując niepowodzenie ładowania zestawów. W tej sytuacji opcja Caspol.exe **-all -reset** nie naprawi zabezpieczeń. W celu naprawienia zabezpieczeń należy ręcznie wyedytować pliki zabezpieczeń, aby usunąć niestandardowy obiekt zabezpieczeń.|  
|**-addgroup** {*parent_label &#124; parent_name*} pset_name *[* *flags*]<br /><br /> lub<br /><br /> **-ag** {*parent_label &#124; parent_name*} pset_name *mship* [*flags*]|Dodaje nową grupę kodu do hierarchii grup kodu. Można określić *parent_label* lub *parent_name*. *Argument parent_label* określa etykietę (np. 1. lub 1.1.) grupy kodu, która jest elementem nadrzędnym dodawanych grup kodu. *Argument parent_name* określa nazwę grupy kodu, która jest elementem nadrzędnym dodawanych grup kodu. Ponieważ *parent_label* i *parent_name* mogą być używane zamiennie, Caspol.exe musi być w stanie odróżnić je. W związku z tym *parent_name* nie może zaczynać się od liczby. Ponadto *parent_name* może zawierać tylko A-Z, 0-9 i znak podkreślenia.<br /><br /> Argument *mship* określa warunek członkostwa dla nowej grupy kodu. Aby uzyskać więcej informacji, zobacz tabelę argumentów *mship* w dalszej części tej sekcji.<br /><br /> *Argument pset_name* to nazwa zestawu uprawnień, który będzie skojarzony z nową grupą kodu. Można również ustawić jedną lub więcej *flag* dla nowej grupy. Aby uzyskać więcej informacji, zobacz tabelę argumentów *flag* w dalszej części tej sekcji.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> lub<br /><br /> **-ap** {*nazwany*_*psfile* &#124; *psfile* *pset_name*}|Dodaje nowy, nazwany zestaw uprawnień do zasad. Zestaw uprawnień musi być w formacie XML i być zapisany w pliku xml. Jeśli plik XML zawiera nazwę zestawu uprawnień, określono tylko ten plik (*psfile).* Jeśli plik XML nie zawiera nazwy zestawu uprawnień, należy określić zarówno nazwę pliku XML (*psfile),* jak i nazwę zestawu uprawnień (*pset_name*).<br /><br /> Należy zauważyć, że wszystkie uprawnienia użyte w zestawie uprawnień muszą być zdefiniowane w zestawie zawartym w globalnej pamięci podręcznej zestawów.|  
|**-a**[**ll**]|Wskazuje, że wszystkie opcje następujące po niej mają zastosowanie do zasad komputera, użytkownika i przedsiębiorstwa. Opcja **-all** zawsze odnosi się do zasad aktualnie zalogowanego użytkownika. Zobacz **-customall** opcja odwoływać się do zasad użytkownika użytkownika innego niż bieżący użytkownik.|  
|**-chggroup** {*nazwa &#124;etykiety*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flagi* `}`<br /><br /> lub<br /><br /> **-cg** {*nazwa &#124;etykiety*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flagi* `}`|Zmienia warunek członkostwa grupy kodu, zestaw uprawnień lub ustawienia **wyłącznych**flag **wyłącznych, levelfinal**, **name**lub **description.** Można określić *etykietę* lub *nazwę*. Argument *label* określa etykietę (np. lub 1.1.) grupy kodów. Argument *name* określa nazwę grupy kodu do zmiany. Ponieważ *etykieta* i *nazwa* mogą być używane zamiennie, Caspol.exe musi być w stanie odróżnić je. W związku z tym *nazwa* nie może zaczynać się od liczby. Ponadto *nazwa* może zawierać tylko A-Z, 0-9 i znak podkreślenia.<br /><br /> *Argument pset_name* określa nazwę zestawu uprawnień do skojarzenia z grupą kodu. Zobacz tabele w dalszej części tej sekcji, aby uzyskać informacje na temat *argumentów mship* i *flag.*|  
|**-chgpset**  *psfile pset_name*<br /><br /> lub<br /><br /> **-cp** *psfile pset_name*|Zmienia nazwany zestaw uprawnień. Argument *psfile* dostarcza nową definicję zestawu uprawnień; jest to plik zestawu uprawnień szeregowych w formacie XML. Argument *pset_name* określa nazwę zestawu uprawnień, który chcesz zmienić.|  
|**-customall**  *ścieżka*<br /><br /> lub<br /><br /> **ścieżka -ca***path*  |Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do zasad komputera, przedsiębiorstwa i określonych niestandardowych zasad użytkownika. Należy określić lokalizację pliku konfiguracji zabezpieczeń użytkownika niestandardowego za pomocą argumentu *path.*|  
|**-cu**[**stomuser**] *ścieżka*|Umożliwia administrację niestandardowymi zasadami użytkownika, które nie należą do użytkownika, w którego imieniu program Caspol.exe jest aktualnie uruchomiony. Należy określić lokalizację pliku konfiguracji zabezpieczeń użytkownika niestandardowego za pomocą argumentu *path.*|  
|**-przedsiębiorstwo**<br /><br /> lub<br /><br /> **-pl**|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad przedsiębiorstwa. Użytkownicy, którzy nie są administratorami przedsiębiorstwa, nie posiadają wystarczających praw, aby modyfikować zasady przedsiębiorstwa, jednak mogą je wyświetlać. W scenariuszach bez przedsiębiorstwa zasady te domyślnie nie kolidują z zasadami komputera i użytkownika.|  
|**-e**[**xecution**] {**na** &#124; **wyłączony }**|Włącza lub wyłącza mechanizm sprawdzający uprawnienia uruchamiania przed rozpoczęciem wykonywania kodu. **Uwaga:**  Ten przełącznik jest usuwany w .NET Framework 4 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [Zmiany zabezpieczeń](../security/security-changes.md).|  
|**-f**[**orce**]|Pomija test samolikwidacji narzędzia i zmienia zasady określone przez użytkownika. Normalnie Caspol.exe sprawdza, czy dowolne zmiany zasad mogą uniemożliwić programowi Caspol.exe poprawne działanie; jeśli tak, Caspol.exe nie zapisze zmian zasad i wyświetli komunikat o błędzie. Aby wymusić na caspol.exe zmianę zasad, nawet jeśli uniemożliwia to uruchomienie caspol.exe, użyj opcji **-force.**|  
|**-h**[**elp**]|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
|**-l**[**ist**]|Wypisuje hierarchię grup kodu i zestawy uprawnień dla określonego komputera, użytkownika, przedsiębiorstwa lub wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listdescription**<br /><br /> lub<br /><br /> **-ld**|Wypisuje opisy wszystkich grup kodu dla określonego poziomu zasad.|  
|**-listfulltrust**<br /><br /> lub<br /><br /> **-lf**|Wypisuje zawartość listy zestawów o pełnym zaufaniu dla określonego poziomu zasad.|  
|**-grupy list**<br /><br /> lub<br /><br /> **-lg**|Wypisuje grupy kodu dla określonego poziomu zasad lud dla wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listpset** lub **-lp**|Wyświetla zestawy uprawnień dla określonego poziomu zasad lub poziomów zasad.|  
|**-m**[**achine**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad komputera. Użytkownicy, którzy nie są administratorami, nie posiadają wystarczających praw, aby modyfikować zasady komputera, jednak mogą je wyświetlać. Dla administratorów **-machine** jest wartością domyślną.|  
|**-polchgprompt** {**na** &#124; **wyłączony }**<br /><br /> lub<br /><br /> **-pp** {**na** &#124; **wyłączony**}|Włącza lub wyłącza monit, który jest wyświetlany zawsze, gdy Caspol.exe jest uruchamiany z opcją powodującą zmianę zasad.|  
|**-quiet**<br /><br /> lub<br /><br /> **-q**|Tymczasowo wyłącza monit, który jest normalnie wyświetlany dla opcji powodującej zmianę zasad. Globalne ustawienie monitu nie jest zmieniane. Należy użyć tej opcji w pojedynczym poleceniu, aby uniknąć wyłączenia monitu dla wszystkich poleceń Caspol.exe.|  
|**-r**[**ecover**]|Odzyskuje zasady z pliku kopii zapasowej. Zawsze, gdy zmieniane są zasady, Caspol.exe zapisuje stare zasady w pliku kopii zapasowej.|  
|**-remfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-rf**  *assembly_file*|Usuwa zestaw z listy zestawów o pełnym zaufaniu poziomu zasad. Ta operacja powinna być wykonana, jeśli zestaw uprawnień, który zawiera niestandardowe uprawnienie, nie jest już dłużej używany przez zasady. Jednakże, należy usunąć zestaw, który implementuje niestandardowe uprawnienie z listy o pełnym zaufaniu, tylko wtedy, gdy zestaw nie implementuje żadnych innych niestandardowych uprawnień, które nadal są używane. Po usunięciu zestawu z listy, należy także usunąć wszystkie inne zależne zestawy.|  
|**-remgroup** {*nazwa &#124;etykiety*}<br /><br /> lub<br /><br /> **-rg** {l*abel &#124; nazwa*}|Usuwa grupę kodu określoną za pomocą nazwy lub etykiety. Jeżeli określona grupa kodu posiada podrzędne grupy kodu, Caspol.exe usunie także wszystkie podrzędne grupy kodu.|  
|**-rempset** *pset_name*<br /><br /> lub<br /><br /> **-rp** *pset_name*|Usuwa określony zestaw uprawnień z zasad. Argument *pset_name* wskazuje, które uprawnienia mają być usuwane. Caspol.exe usuwa zestaw uprawnień tylko wtedy, gdy nie jest skojarzony z żadną grupą kodu. Domyślne (wbudowane) zestawy uprawnień nie mogą zostać usunięte.|  
|**-reset**<br /><br /> lub<br /><br /> **-rs**|Przywraca zasadom domyślny stan i zapisuje je na dysku. Jest to użyteczne, gdy zmienione zasady są nie do naprawienia i trzeba rozpocząć od nowa, z domyślnymi ustawieniami instalacji. Resetowanie może być również wygodne, gdy zachodzi potrzeba użycia domyślnych zasad jako punktu początkowego do modyfikacji określonych plików konfiguracji zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Ręczne edytowanie plików konfiguracji zabezpieczeń](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> lub<br /><br /> **-rsld**|Zwraca zasadę do bardziej restrykcyjnej wersji stanu domyślnego i utrzymuje ją na dysku; tworzy kopię zapasową poprzedniej zasady komputera i utrzymuje `security.config.bac`ją w pliku o nazwie .  Zablokowane zasady są podobne do zasad domyślnych, z tą różnicą, `Local Intranet` `Trusted Sites`że `Internet` zasada nie udziela uprawnień do kodu z , i stref i odpowiednich grup kodu nie mają grup kodów podrzędnych.|  
|**-assembly_file grupy rozwiązywania** *assembly_file*<br /><br /> lub<br /><br /> **-rsg**  *assembly_file*|Pokazuje grupy kodów, do których należy określony zestaw (*assembly_file).* Domyślnie ta opcja wyświetla poziomy zasad komputera, użytkownika i przedsiębiorstwa, do których należy zestaw. Aby wyświetlić tylko jeden poziom zasad, użyj tej opcji z opcją **-machine**, **-user**lub **-enterprise.**|  
|**-assembly_file assembly_file** *assembly_file*<br /><br /> lub<br /><br /> **-rsp** *assembly_file*|Wyświetla wszystkie uprawnienia, które zostaną przydzielone zestawowi, przez określony (lub domyślny) poziom zasad bezpieczeństwa, gdyby zestaw mógł być uruchomiony. *Argument assembly_file* określa zestaw. Jeśli określisz opcję **-all,** caspol.exe oblicza uprawnienia do zestawu na podstawie zasad użytkownika, komputera i przedsiębiorstwa; w przeciwnym razie obowiązują domyślne reguły zachowania.|  
|**-s**[**ecurity**] {**na** &#124; **wyłączony }**|Włącza lub wyłącza zabezpieczenia dostępu kodu. Określenie opcji **-s off** nie powoduje wyłączenia zabezpieczeń opartych na rolach. **Uwaga:**  Ten przełącznik jest usuwany w .NET Framework 4 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [Zmiany zabezpieczeń](../security/security-changes.md). **Uwaga:**  Gdy zabezpieczenia dostępu do kodu są wyłączone, wszystkie żądania dostępu do kodu powiodą się. Wyłączenie zabezpieczeń dostępu kodu sprawia, że system staje się podatny na ataki złośliwego kodu, takiego jak wirusy i robaki. Wyłączenie zabezpieczeń wpływa na zwiększenie wydajności, ale powinno być stosowane tylko wtedy, gdy zastosowano wszelkie inne zabezpieczenia, aby zapewnić, że ogólne zabezpieczenia systemu nie zostały naruszone. Przykłady innych środków ostrożności to: odłączenie od sieci publicznych, fizyczne zabezpieczanie komputerów i tak dalej.|  
|**-u**[**ser**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad użytkownika, w którego imieniu Caspol.exe jest uruchomiony. Dla użytkowników nienadnadistracyjnych **- użytkownik** jest ustawieniem domyślnym.|  
|**-?**|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
  
 Argument *mship,* który określa warunek członkostwa dla grupy kodu, może być używany z **opcjami -addgroup** i **-chggroup.** Każdy argument *mship* jest implementowany jako klasa .NET Framework. Aby określić *mship,* należy użyć jednej z następujących czynności.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**-allcode**|Określa cały kod. Aby uzyskać więcej informacji na <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>temat tego warunku członkostwa, zobacz .|  
|**-appdir**|Określa katalog aplikacji. Jeśli określisz **-appdir** jako warunek członkostwa, dowód adresów URL kodu jest porównywany z dowodami katalogu aplikacji tego kodu. Jeśli obie wartości są takie same, warunek członkostwa jest spełniony. Aby uzyskać więcej informacji na <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>temat tego warunku członkostwa, zobacz .|  
|**-niestandardowy**  *plik xml*|Dodaje niestandardowy warunek członkostwa. Obowiązkowy argument *xmlfile* określa plik xml zawierający serializację XML niestandardowego warunku członkostwa.|  
|**-hash** *hashAlg* {**-hex** *hashValue* &#124; **-file** *assembly_file* }|Określa kod, który posiada podany skrót zestawu. Aby użyć skrótu jako warunku członkostwa grupy kodu, należy określić wartość skrótu lub plik zestawu. Aby uzyskać więcej informacji na <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>temat tego warunku członkostwa, zobacz .|  
|**-pub** { **-cert** *cert_file_name* &#124;<br /><br /> **-plik** *signed_file_name* &#124; **-hex**  *hex_string* }|Określa kod, który posiada podanego wydawcę oprogramowania wskazanego przez plik certyfikatu, sygnaturę pliku lub reprezentację szesnastkową certyfikatu X509. Aby uzyskać więcej informacji na <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>temat tego warunku członkostwa, zobacz .|  
|**-strona** *internetowa*|Określa kod, który posiada określoną witrynę pochodzenia. Przykład:<br /><br /> `-site** www.proseware.com`<br /><br /> Aby uzyskać więcej informacji na <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>temat tego warunku członkostwa, zobacz .|  
|**-strong -file** *file_name* {*name* &#124; **-noname**} {*version* &#124; **-noversion**}|Określa kod, który ma określoną silną nazwę, określoną przez nazwę pliku, nazwę zestawu jako ciąg i wersję zestawu w formacie *głównym*. *drobne*. *budować*. *rewizji*. Przykład:<br /><br /> **-silny -file** myAssembly.exe myAssembly 1.2.3.4<br /><br /> Aby uzyskać więcej informacji na <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>temat tego warunku członkostwa, zobacz .|  
|**-url** *URL*|Określa kod, który pochodzi z określonego adresu URL. Adres URL musi zawierać protokół, taki jak `http://` lub `ftp://`. Ponadto symbol wieloznaczny\*( ) może służyć do określania wielu zestawów z określonego adresu URL. **Uwaga:**  Ponieważ adres URL można zidentyfikować przy użyciu wielu nazw, przy użyciu adresu URL jako warunek członkostwa nie jest bezpieczny sposób ustalenia tożsamości kodu. Gdy jest to możliwe, należy używać silnej nazwy jako warunku członkostwa, wydawcy jako warunku członkostwa lub skrótu jako warunku członkostwa. <br /><br /> Aby uzyskać więcej informacji na <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>temat tego warunku członkostwa, zobacz .|  
|**-nazwa** *strefy*|Określa kod, który pochodzi z określonej strefy. Argument *zonename* może być jedną z następujących wartości: **MyComputer**, **Intranet**, **Trusted**, **Internet**lub **Niezaufane**. Aby uzyskać więcej informacji na <xref:System.Security.Policy.ZoneMembershipCondition> temat tego warunku członkostwa, zobacz Class.|  
  
 Argument *Flags,* który może być używany z opcjami **–addgroup** i **–chggroup,** jest określony przy użyciu jednego z następujących opcji.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**-opis** "*opis*"|Jeśli jest używana z opcją **–addgroup,** określa opis grupy kodu do dodania. Jeśli jest używana z opcją **–chggroup,** określa opis grupy kodu do edycji. Argument *opisu* musi być ujęty w cudzysłowie.|  
|**-exclusive** {**na**&#124;**wyłączony**}|Po ustawieniu **na**, wskazuje, że tylko zestaw uprawnień skojarzony z grupą kodu, którą dodajesz lub modyfikujesz, jest brany pod uwagę, gdy niektóre kody pasują do warunku członkostwa grupy kodu. Gdy ta opcja jest ustawiona na **wyłączenie,** caspol.exe uwzględnia zestawy uprawnień wszystkich pasujących grup kodów na poziomie zasad.|  
|**-levelfinal** {**na**&#124;**wyłączony**}|Po ustawieniu **na ,** wskazuje, że nie uwzględnia się poziomu zasad poniżej poziomu, w którym występuje dodana lub zmodyfikowana grupa kodu. Ta opcja jest typowo używana na poziomie zasad komputera. Na przykład, jeśli flaga grupy kodu ustawiona będzie na poziom komputera i jakiś kod odpowiada warunkowi członkostwa grupy kodu, Caspol.exe nie oblicza ani nie stosuje zasad poziomu użytkownika dla tego kodu.|  
|**-nazwa** "*name*"|Jeśli jest używana z opcją **–addgroup,** określa nazwę skryptów dla grupy kodu do dodania. Jeśli jest używana z opcją **-chggroup,** określa nazwę skryptów dla grupy kodu do edycji. Argument *name* musi być ujęty w cudzysłowie. Argument *name* nie może zaczynać się od liczby i może zawierać tylko A-Z, 0-9 i znak podkreślenia. Grupy kodu mogą być odwoływane przez tę *nazwę,* a nie ich etykiety numerycznej. *Nazwa* jest również bardzo przydatna do celów skryptów.|  
  
## <a name="remarks"></a>Uwagi  
 Zasady zabezpieczeń są wyrażone za pomocą trzech poziomów zasad: zasady komputera, zasady użytkownika i zasady przedsiębiorstwa. Zestaw uprawnień otrzymanych przez zestaw jest określony przez przecięcie zestawów uprawnień dopuszczonych przez trzy poziomy zasad. Każdy poziom zasad jest reprezentowany przez hierarchiczną strukturę grup kodu. Każda grupa kodu posiada warunek członkostwa, który określa, jaki kod jest członkiem tej grupy. Nazwany zestaw uprawnień jest również skojarzony z każdą grupą kodu. Ten zestaw uprawnień określa uprawnienia, które spełniają warunek członkostwa, jakie środowisko uruchomieniowe przydziela kodowi. Hierarchia grup kodu ze skojarzonymi nazwanymi zestawami uprawnień definiuje i utrzymuje każdy poziom zasad zabezpieczeń. Można użyć opcji **–user**, **-customuser**, **-machine** i **-enterprise,** aby ustawić poziom zasad zabezpieczeń.  
  
 Aby uzyskać więcej informacji na temat zasad zabezpieczeń i sposobu, w jaki środowisko wykonawcze określa uprawnienia do przyznania kodu, zobacz [Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odwoływanie się do grup kodu i zestawów uprawnień  
 Aby ułatwić odwoływanie się do grup kodu w hierarchii, opcja **-list** wyświetla wciętą listę grup kodów wraz z ich etykietami numerycznymi (1, 1.1, 1.1.1 i tak dalej). Inne operacje wiersza polecenia przeznaczone dla grup kodu także używają etykiet liczbowych, aby odwołać się do określonej grupy kodu.  
  
 Odwołania do nazwanych zestawów uprawnień możliwe są przy użyciu ich nazw. Opcja **–list** wyświetla listę grup kodów, po których następuje lista nazwanych zestawów uprawnień dostępnych w tych zasadach.  
  
## <a name="caspolexe-behavior"></a>Zachowanie Caspol.exe  
 Wszystkie opcje z wyjątkiem **-s**[**ecurity**] {**na** &#124; **off**} używają wersji programu .NET Framework, z którą zainstalowano program Caspol.exe. Po uruchomieniu caspol.exe, który został zainstalowany w wersji *X* środowiska wykonawczego, zmiany dotyczą tylko tej wersji. Inne instalacje środowiska uruchomieniowego, jeśli są, nie zostaną uwzględnione. Jeżeli program Caspol.exe jest uruchamiany w wierszu poleceń poza katalogiem określonej wersji środowiska uruchomieniowego, narzędzie jest wykonywane w pierwszym katalogu wersji środowiska uruchomieniowego w ścieżce (zazwyczaj ostatnio zainstalowane środowisko uruchomieniowe).  
  
 Opcja **-s**[**ecurity**] {**on** &#124; **off }** jest operacją całego komputera. Wyłączenie zabezpieczeń dostępu kodu przerywa sprawdzenia zabezpieczeń dla całego kodu zarządzanego i dla wszystkich użytkowników komputera. Jeżeli jest zainstalowanych wiele wersji platformy .NET Framework, to polecenie wyłączy zabezpieczenia dla każdej zainstalowanej wersji na komputerze. Chociaż opcja **-list** pokazuje, że zabezpieczenia są wyłączone, nic innego wyraźnie nie wskazuje innym użytkownikom, że zabezpieczenia zostały wyłączone.  
  
 Gdy użytkownik bez uprawnień administracyjnych uruchamia plik Caspol.exe, wszystkie opcje odnoszą się do zasad na poziomie użytkownika, chyba że określono opcję **–komputer.** Gdy administrator uruchamia program Caspol.exe, wszystkie opcje odnoszą się do zasad komputera, chyba że określono opcję **–user.**  
  
 Caspol.exe musi mieć odpowiednik **wszystko** ustawionego uprawnienia do działania. Narzędzie posiada mechanizm zabezpieczający, który uniemożliwia modyfikowanie zasad w sposób uniemożliwiający udzielenia Caspol.exe uprawnień, których potrzebuje do uruchomienia. Podczas próby zmiany ustawień program Caspol.exe powiadamia, że żądana zmiana zasad spowoduje awarię narzędzia i zmiana zasad zostanie odrzucona. Ten mechanizm ochronny można wyłączyć dla danego polecenia za pomocą opcji **-force.**  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>
## <a name="manually-editing-the-security-configuration-files"></a>Ręczna edycja plików konfiguracji zabezpieczeń  
 Trzy pliki konfiguracji zabezpieczeń odnoszą się do trzech poziomów zabezpieczeń obsługiwanych przez Caspol.exe: jeden dla zasad komputera, jeden dla podanego użytkownika i jeden dla zasad przedsiębiorstwa. Te trzy pliki są tworzone na dysku tylko wtedy, gdy zasady komputera, użytkownika lub przedsiębiorstwa są zmienione za pomocą Caspol.exe. Za pomocą opcji **Reset w** pliku Caspol.exe można w razie potrzeby zapisać domyślne zasady zabezpieczeń na dysku.  
  
 W większości przypadków ręczna edycja plików konfiguracji zabezpieczeń nie jest zalecana. Jednak mogą pojawić się scenariusze, w których modyfikowanie tych plików może być konieczne, na przykład gdy administrator chce edytować konfigurację zabezpieczeń dla określonego użytkownika.  
  
## <a name="examples"></a>Przykłady  
 **-addfulltrust**  
  
 Zakłada, że zestaw uprawnień zawierający niestandardowe uprawnienie został dodany do zasad komputera. To uprawnienie niestandardowe `MyPerm.exe`jest `MyPerm.exe` implementowane `MyOther.exe`w sekcji , i odwołuje się do klas w . Oba zestawy muszą być dodane do listy zestawów o pełnym zaufaniu. Następujące polecenie dodaje `MyPerm.exe` zestaw do pełnej listy zaufania dla zasad komputera.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Następujące polecenie dodaje `MyOther.exe` zestaw do pełnej listy zaufania dla zasad komputera.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Następujące polecenie dodaje podrzędną grupę kodu do korzenia hierarchii grup kodu zasad komputera. Nowa grupa kodu jest członkiem strefy **Internet** i jest skojarzona z zestawem uprawnień **Wykonanie.**  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Następujące polecenie dodaje podrzędną grupę \\kodów, która daje udział \netserver\netshare lokalne uprawnienia intranetowe.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Następujące polecenie dodaje `Mypset` zestaw uprawnień do zasad użytkownika.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-grupa chg**  
  
 Następujące polecenie zmienia uprawnienia ustawione w zasadach użytkownika grupy kodu oznaczonej jako 1.2. do zestawu uprawnień **Wykonanie.**  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Następujące polecenie zmienia warunek członkostwa w domyślnych zasadach grupy kodu oznaczonych jako 1.2.1. i zmienia ustawienie **wyłącznej** flagi. Warunek członkostwa jest zdefiniowany jako kod, który pochodzi ze strefy **Internet** i **wyłącznej** flagi jest włączona.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Następujące polecenie zmienia zestaw uprawnień z nazwą `Mypset` na `newpset.xml`zestaw uprawnień zawarty w pliku . Należy zauważyć, że aktualne wydanie nie obsługuje zmiany zestawów uprawnień, które są używane przez hierarchię grup kodu.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-siła**  
  
 Następujące polecenie powoduje, że główna grupa kodu zasad użytkownika (oznaczona etykietą 1) ma być skojarzona z zestawem uprawnień **Nothing** named. Uniemożliwia to uruchomienie programu Caspol.exe.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-odzyskać**  
  
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
  
 Następujące polecenie usuwa zestaw uprawnień **Wykonanie** z zasad użytkownika.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Następujące polecenie usuwa `Mypset` z poziomu zasad użytkownika.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-grupa rozwiązywania problemów**  
  
 Następujące polecenie pokazuje wszystkie grupy kodów `myassembly` zasad komputera, do których należy.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Następujące polecenie pokazuje wszystkie grupy kodu komputera, przedsiębiorstwa i `myassembly` określone niestandardowe zasady użytkownika, do których należy.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Następujące polecenie oblicza uprawnienia `testassembly` dla na podstawie poziomu zasad komputera i użytkownika.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
