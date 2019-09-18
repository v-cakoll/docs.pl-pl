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
ms.openlocfilehash: bc4dd2703f32f2983a207d5990a6e8e646de8c17
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044861"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (Narzędzie zasad zabezpieczeń dostępu kodu)
Narzędzie (Caspol.exe) sprawdzania zabezpieczeń dostępu kodu (CAS) pozwala użytkownikom i administratorom na modyfikowanie zasad bezpieczeństwa na poziomie zasad komputera, na poziomie zasad użytkownika i na poziomie zasad przedsiębiorstwa.  
  
> [!IMPORTANT]
> Począwszy od .NET Framework 4, Caspol. exe nie wpływa na zasady dotyczące urzędów certyfikacji, `true` [ \<chyba że element > legacyCasPolicy](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) jest ustawiony na. Wszelkie ustawienia pokazywane lub modyfikowane przez narzędzie CasPol.exe wpływają tylko na aplikacje, w których są stosowane zasady CAS. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../security/security-changes.md).  
  
> [!NOTE]
> Na komputerach 64-bitowych dostępne są obie, 32-bitowa i 64-bitowa, wersje zasad zabezpieczeń. Aby upewnić się, że zmiany zasad mają zastosowanie do obu, 32-bitowych i 64-bitowych aplikacji, należy uruchomić obie, 32-bitową i 64-bitową, wersję Caspol.exe.  
  
 Narzędzie sprawdzania zabezpieczeń dostępu kodu jest automatycznie instalowane z .NET Framework i z programem Visual Studio. Caspol. exe można znaleźć w*wersji* %windir%\Microsoft.NET\Framework\\w systemach 32-bitowych lub w*wersji* %windir%\Microsoft.NET\Framework64\\w systemach 64-bitowych. (Na przykład lokalizacja to %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe dla .NET Framework 4 w systemach 64-bitowych). Może być zainstalowanych wiele wersji narzędzia, jeżeli komputer używa równolegle wielu wersji platformy .NET Framework. Narzędzie można uruchomić z katalogu instalacji. Zaleca się jednak używanie [monitów polecenia](developer-command-prompt-for-vs.md), które nie wymagają przejścia do folderu instalacji.  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console
caspol [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-AF** *assembly_file*|Dodaje zestaw, który implementuje niestandardowy obiekt zabezpieczeń (taki jak niestandardowe uprawnienia lub niestandardowe warunki członkostwa), do listy zestawów o pełnym zaufaniu dla specyficznego poziomu zasad. Argument *assembly_file* określa zestaw, który ma zostać dodany. Ten plik musi być podpisany za pomocą [silnej nazwy](../../standard/assembly/strong-named.md). Można podpisać zestaw za pomocą silnej nazwy przy użyciu [Narzędzia silnej nazwy (SN. exe)](sn-exe-strong-name-tool.md).<br /><br /> Za każdym razem, gdy zestaw uprawnień zawierający niestandardowe uprawnienia jest dodawany do zasad, zestaw implementujący niestandardowe uprawnienia musi zostać dodany do listy zestawów o pełnym zaufaniu dla danego poziomu zasad. Zestawy, które implementują niestandardowe obiekty zabezpieczeń (takie jak niestandardowe grupy kodu lub warunki członkostwa) używane w zasadach zabezpieczeń (takich jak zasady komputera) powinny być zawsze dodawane do listy zestawów pełnego zaufania. **Ostrzeżenie**  Jeśli zestaw implementujący niestandardowe obiekty zabezpieczeń odwołuje się do innych zestawów, należy najpierw dodać do listy zestawów o pełnym zaufaniu zestawy, do których ma miejsce odwołanie. Niestandardowe obiekty zabezpieczeń stworzone za pomocą języków Visual Basic, C++ i JScript odwołują się odpowiednio do Microsoft.VisualBasic.dll, Microsoft.VisualC.dll lub Microsoft.JScript.dll. Zestawy te nie znajdują się domyślnie na liście zestawów o pełnym zaufaniu. Należy dodać odpowiedni zestaw do listy o pełnym zaufaniu przed dodaniem niestandardowego obiektu zabezpieczeń. Niewykonanie tej czynności spowoduje awarię systemu zabezpieczeń, powodując niepowodzenie ładowania zestawów. W takiej sytuacji opcja Caspol. exe **-All-Reset** nie naprawia zabezpieczeń. W celu naprawienia zabezpieczeń należy ręcznie wyedytować pliki zabezpieczeń, aby usunąć niestandardowy obiekt zabezpieczeń.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*flagi*]<br /><br /> lub<br /><br /> **-AG** {*parent_label &#124; parent_name*} *mship pset_name* [*flagi*]|Dodaje nową grupę kodu do hierarchii grup kodu. Można określić wartość *parent_label* lub *parent_name*. Argument *parent_label* Określa etykietę (taką jak 1. lub 1,1). grupy kodu, która jest elementem nadrzędnym dodawanej grupy kodu. Argument *parent_name* określa nazwę grupy kodu, która jest elementem nadrzędnym dodawanej grupy kodu. Ponieważ *parent_label* i *parent_name* mogą być używane zamiennie, Caspol. exe musi mieć możliwość rozróżnienia między nimi. W związku z tym *parent_name* nie może rozpoczynać się od cyfry. Ponadto *parent_name* może zawierać tylko znaki a-z, 0-9 i znak podkreślenia.<br /><br /> Argument *mship* określa warunek członkostwa dla nowej grupy kodu. Aby uzyskać więcej informacji, zobacz tabelę argumentów *mship* w dalszej części tej sekcji.<br /><br /> Argument *pset_name* jest nazwą zestawu uprawnień, który zostanie skojarzony z nową grupą kodu. Można również ustawić jedną lub więcej *flag* dla nowej grupy. Aby uzyskać więcej informacji, zobacz tabelę argumentów *flag* w dalszej części tej sekcji.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> lub<br /><br /> **-ap** {*named*_*psfile* &#124; *psfile* *pset_name*}|Dodaje nowy, nazwany zestaw uprawnień do zasad. Zestaw uprawnień musi być w formacie XML i być zapisany w pliku xml. Jeśli plik XML zawiera nazwę zestawu uprawnień, określony jest tylko ten plik (*psfile*). Jeśli plik XML nie zawiera nazwy zestawu uprawnień, należy określić zarówno nazwę pliku XML (*psfile*), jak i nazwę zestawu uprawnień (*pset_name*).<br /><br /> Należy zauważyć, że wszystkie uprawnienia użyte w zestawie uprawnień muszą być zdefiniowane w zestawie zawartym w globalnej pamięci podręcznej zestawów.|  
|**-a**[**ll**]|Wskazuje, że wszystkie opcje następujące po niej mają zastosowanie do zasad komputera, użytkownika i przedsiębiorstwa. Opcja **-All** zawsze odwołuje się do zasad aktualnie zalogowanego użytkownika. Zapoznaj się z opcją **-customall** , aby odwołać się do zasad użytkownika innego niż bieżący użytkownik.|  
|**-chggroup** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flagi*`}`<br /><br /> lub<br /><br /> **-cg** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *flagi*`}`|Zmienia warunek członkostwa grupy kodu, zestaw uprawnień lub ustawienia dla flag **wyłączne**, **levelfinal**, **name**i **Description** . Można określić *etykietę* lub *nazwę*. Argument *Label* Określa etykietę (taką jak 1). lub 1,1). grupy kodu. Argument *name* określa nazwę grupy kodu do zmiany. Ponieważ *etykiety* i *nazwy* mogą być używane zamiennie, Caspol. exe musi mieć możliwość rozróżnienia między nimi. W związku z tym *Nazwa* nie może rozpoczynać się od cyfry. Ponadto *Nazwa* może zawierać tylko znaki a-z, 0-9 i znak podkreślenia.<br /><br /> Argument *pset_name* określa nazwę zestawu uprawnień, który ma zostać skojarzony z grupą kodu. Zapoznaj się z tabelami w dalszej części tej sekcji, aby uzyskać informacje na temat argumentów *mship* i *flags* .|  
|**-chgpset** *psfile pset_name*<br /><br /> lub<br /><br /> **-CP** *psfile pset_name*|Zmienia nazwany zestaw uprawnień. Argument *psfile* dostarcza nową definicję zestawu uprawnień; jest to serializowany plik zestawu uprawnień w formacie XML. Argument *pset_name* określa nazwę zestawu uprawnień, który ma zostać zmieniony.|  
|**-customall** *ścieżki*<br /><br /> lub<br /><br /> **-ca** *ścieżki*|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do zasad komputera, przedsiębiorstwa i określonych niestandardowych zasad użytkownika. Należy określić lokalizację pliku konfiguracji zabezpieczeń niestandardowego użytkownika z argumentem *Path* .|  
|**-cu** [**stomuser**] *ścieżka*|Umożliwia administrację niestandardowymi zasadami użytkownika, które nie należą do użytkownika, w którego imieniu program Caspol.exe jest aktualnie uruchomiony. Należy określić lokalizację pliku konfiguracji zabezpieczeń niestandardowego użytkownika z argumentem *Path* .|  
|**-enterprise**<br /><br /> lub<br /><br /> **-pl**|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad przedsiębiorstwa. Użytkownicy, którzy nie są administratorami przedsiębiorstwa, nie posiadają wystarczających praw, aby modyfikować zasady przedsiębiorstwa, jednak mogą je wyświetlać. W scenariuszach bez przedsiębiorstwa zasady te domyślnie nie kolidują z zasadami komputera i użytkownika.|  
|**-e** [**xecution**] {**on** &#124; **off**}|Włącza lub wyłącza mechanizm sprawdzający uprawnienia uruchamiania przed rozpoczęciem wykonywania kodu. **Uwaga:**  Ten przełącznik jest usuwany w .NET Framework 4 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../security/security-changes.md).|  
|**-f** [**Orce**]|Pomija test samolikwidacji narzędzia i zmienia zasady określone przez użytkownika. Normalnie Caspol.exe sprawdza, czy dowolne zmiany zasad mogą uniemożliwić programowi Caspol.exe poprawne działanie; jeśli tak, Caspol.exe nie zapisze zmian zasad i wyświetli komunikat o błędzie. Aby wymusić zmianę zasad przez Caspol. exe, nawet jeśli uniemożliwia to uruchomienie programu Caspol. exe, użyj opcji **– Force** .|  
|**-h** [**ELP**]|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
|**-l**[**ist**]|Wypisuje hierarchię grup kodu i zestawy uprawnień dla określonego komputera, użytkownika, przedsiębiorstwa lub wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listdescription**<br /><br /> lub<br /><br /> **-LD**|Wypisuje opisy wszystkich grup kodu dla określonego poziomu zasad.|  
|**-listfulltrust**<br /><br /> lub<br /><br /> **-lf**|Wypisuje zawartość listy zestawów o pełnym zaufaniu dla określonego poziomu zasad.|  
|**-listgroups**<br /><br /> lub<br /><br /> **-lg**|Wypisuje grupy kodu dla określonego poziomu zasad lud dla wszystkich poziomów zasad. Caspol.exe wyświetla najpierw etykietę grupy kodu, następnie nazwę, jeśli nie jest pusta.|  
|**-listpset** lub **-LP**|Wyświetla zestawy uprawnień dla określonego poziomu zasad lub poziomów zasad.|  
|**-m** [**achine**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad komputera. Użytkownicy, którzy nie są administratorami, nie posiadają wystarczających praw, aby modyfikować zasady komputera, jednak mogą je wyświetlać. W przypadku administratorów wartość domyślna to **Machine** .|  
|**-polchgprompt** {**on** &#124; **off**}<br /><br /> lub<br /><br /> **-PP** {**on** &#124; **off**}|Włącza lub wyłącza monit, który jest wyświetlany zawsze, gdy Caspol.exe jest uruchamiany z opcją powodującą zmianę zasad.|  
|**-quiet**<br /><br /> lub<br /><br /> **-q**|Tymczasowo wyłącza monit, który jest normalnie wyświetlany dla opcji powodującej zmianę zasad. Globalne ustawienie monitu nie jest zmieniane. Należy użyć tej opcji w pojedynczym poleceniu, aby uniknąć wyłączenia monitu dla wszystkich poleceń Caspol.exe.|  
|**-r** [**Ecover**]|Odzyskuje zasady z pliku kopii zapasowej. Zawsze, gdy zmieniane są zasady, Caspol.exe zapisuje stare zasady w pliku kopii zapasowej.|  
|**-remfulltrust** *assembly_file*<br /><br /> lub<br /><br /> **-rf** *assembly_file*|Usuwa zestaw z listy zestawów o pełnym zaufaniu poziomu zasad. Ta operacja powinna być wykonana, jeśli zestaw uprawnień, który zawiera niestandardowe uprawnienie, nie jest już dłużej używany przez zasady. Jednakże, należy usunąć zestaw, który implementuje niestandardowe uprawnienie z listy o pełnym zaufaniu, tylko wtedy, gdy zestaw nie implementuje żadnych innych niestandardowych uprawnień, które nadal są używane. Po usunięciu zestawu z listy, należy także usunąć wszystkie inne zależne zestawy.|  
|**-remgroup** {*label &#124;name*}<br /><br /> lub<br /><br /> **-RG** {l*Abel &#124; nazwa*}|Usuwa grupę kodu określoną za pomocą nazwy lub etykiety. Jeżeli określona grupa kodu posiada podrzędne grupy kodu, Caspol.exe usunie także wszystkie podrzędne grupy kodu.|  
|**-rempset** *pset_name*<br /><br /> lub<br /><br /> **-RP** *pset_name*|Usuwa określony zestaw uprawnień z zasad. Argument *pset_name* wskazuje zestaw uprawnień, który ma zostać usunięty. Caspol.exe usuwa zestaw uprawnień tylko wtedy, gdy nie jest skojarzony z żadną grupą kodu. Domyślne (wbudowane) zestawy uprawnień nie mogą zostać usunięte.|  
|**-Reset**<br /><br /> lub<br /><br /> **-RS**|Przywraca zasadom domyślny stan i zapisuje je na dysku. Jest to użyteczne, gdy zmienione zasady są nie do naprawienia i trzeba rozpocząć od nowa, z domyślnymi ustawieniami instalacji. Resetowanie może być również wygodne, gdy zachodzi potrzeba użycia domyślnych zasad jako punktu początkowego do modyfikacji określonych plików konfiguracji zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Ręczne edytowanie plików konfiguracji zabezpieczeń](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> lub<br /><br /> **-rsld**|Zwraca zasady do bardziej restrykcyjnej wersji stanu domyślnego i utrzymuje ją na dysku; tworzy kopię zapasową poprzednich zasad komputera i utrzymuje ją w pliku o nazwie `security.config.bac`.  Zablokowane zasady są podobne do zasad domyślnych, z tą różnicą, że zasady nie udzielają uprawnień do kodu z `Local Intranet`, `Trusted Sites`i i `Internet` nie mają żadnych podrzędnych grup kodu.|  
|**-Rozpoznaj** *assembly_file*<br /><br /> lub<br /><br /> **-RSG** *assembly_file*|Pokazuje grupy kodu, do których należy określony zestaw (*assembly_file*). Domyślnie ta opcja wyświetla poziomy zasad komputera, użytkownika i przedsiębiorstwa, do których należy zestaw. Aby wyświetlić tylko jeden poziom zasad, Użyj tej opcji z opcją **-Machine**, **-User**lub **-Enterprise** .|  
|**-resolveperm** *assembly_file*<br /><br /> lub<br /><br /> **-RSP** *assembly_file*|Wyświetla wszystkie uprawnienia, które zostaną przydzielone zestawowi, przez określony (lub domyślny) poziom zasad bezpieczeństwa, gdyby zestaw mógł być uruchomiony. Argument *assembly_file* określa zestaw. Jeśli określisz opcję **-All** , Caspol. exe oblicza uprawnienia dla zestawu na podstawie zasad użytkownika, komputera i przedsiębiorstwa; w przeciwnym razie stosowane są domyślne reguły zachowania.|  
|**-s** [**ecurity**] {**on** &#124; **off**}|Włącza lub wyłącza zabezpieczenia dostępu kodu. Określenie opcji **-s off** nie powoduje wyłączenia zabezpieczeń opartych na rolach. **Uwaga:**  Ten przełącznik jest usuwany w .NET Framework 4 i nowszych wersjach. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../security/security-changes.md). **Ostrzeżenie**  Gdy zabezpieczenia dostępu kodu są wyłączone, wszystkie żądania dostępu do kodu kończą się powodzeniem. Wyłączenie zabezpieczeń dostępu kodu sprawia, że system staje się podatny na ataki złośliwego kodu, takiego jak wirusy i robaki. Wyłączenie zabezpieczeń wpływa na zwiększenie wydajności, ale powinno być stosowane tylko wtedy, gdy zastosowano wszelkie inne zabezpieczenia, aby zapewnić, że ogólne zabezpieczenia systemu nie zostały naruszone. Przykłady innych środków ostrożności to: odłączenie od sieci publicznych, fizyczne zabezpieczanie komputerów i tak dalej.|  
|**-u** [**ser**]|Wskazuje, że wszystkie opcje następujące po niej, mają zastosowanie do poziomu zasad użytkownika, w którego imieniu Caspol.exe jest uruchomiony. Dla użytkowników niebędących administratorami — wartość domyślna to **użytkownika** .|  
|**-?**|Wyświetla składnię polecenia i opcje programu Caspol.exe.|  
  
 Argument *mship* , który określa warunek członkostwa dla grupy kodu, może być używany z opcjami **-addgroup** i **-chggroup** . Każdy argument *mship* jest implementowany jako Klasa .NET Framework. Aby określić *mship,* Użyj jednego z następujących elementów.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**-allcode**|Określa cały kod. Aby uzyskać więcej informacji dotyczących warunku członkostwa, <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>Zobacz.|  
|**-appdir**|Określa katalog aplikacji. Jeśli określisz wartość **– appdir** jako warunek członkostwa, dowód adresu URL kodu jest porównywany z dowodem katalogu aplikacji tego kodu. Jeśli obie wartości są takie same, warunek członkostwa jest spełniony. Aby uzyskać więcej informacji dotyczących warunku członkostwa, <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>Zobacz.|  
|**-niestandardowe** *xmlfile*|Dodaje niestandardowy warunek członkostwa. Obowiązkowy argument *xmlfile* określa plik XML, który zawiera serializacji XML warunku członkostwa niestandardowego.|  
|**-hash** *hashAlg* { **-HEX** *hashValue* &#124; **-File** *assembly_file* }|Określa kod, który posiada podany skrót zestawu. Aby użyć skrótu jako warunku członkostwa grupy kodu, należy określić wartość skrótu lub plik zestawu. Aby uzyskać więcej informacji dotyczących warunku członkostwa, <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>Zobacz.|  
|**-pub** { **-CERT** *cert_file_name*&#124;<br /><br /> **-plik** *signed_file_name* &#124; **-HEX**  *hex_string* }|Określa kod, który posiada podanego wydawcę oprogramowania wskazanego przez plik certyfikatu, sygnaturę pliku lub reprezentację szesnastkową certyfikatu X509. Aby uzyskać więcej informacji dotyczących warunku członkostwa, <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>Zobacz.|  
|**-lokacja** *Witryna sieci Web*|Określa kod, który posiada określoną witrynę pochodzenia. Na przykład:<br /><br /> `-site** www.proseware.com`<br /><br /> Aby uzyskać więcej informacji dotyczących warunku członkostwa, <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>Zobacz.|  
|**-Strong-File** *nazwa_pliku* {*name* &#124; **-NoName**} {*Version* &#124; **-noversion**}|Określa kod, który ma określoną silną nazwę, zgodnie z nazwą pliku, nazwą zestawu jako ciąg i wersję zestawu w formacie *głównym*. *pomocnicze*. *kompilacja*. *poprawka*. Na przykład:<br /><br /> **-Strong-File plik z** zestawem. exe<br /><br /> Aby uzyskać więcej informacji dotyczących warunku członkostwa, <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>Zobacz.|  
|**-URL** *Adres URL*|Określa kod, który pochodzi z określonego adresu URL. Adres URL musi zawierać protokół, taki jak `http://` lub. `ftp://` Ponadto symbol wieloznaczny (\*) może służyć do określenia wielu zestawów z określonego adresu URL. **Uwaga:**  Ponieważ adres URL może być zidentyfikowany za pomocą wielu nazw, używanie adresu URL, jako warunku członkostwa, nie jest bezpieczną metodą ustalania tożsamości kodu. Gdy jest to możliwe, należy używać silnej nazwy jako warunku członkostwa, wydawcy jako warunku członkostwa lub skrótu jako warunku członkostwa. <br /><br /> Aby uzyskać więcej informacji dotyczących warunku członkostwa, <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>Zobacz.|  
|**-strefa** Nr *strefy*|Określa kod, który pochodzi z określonej strefy. Argument *zonename* może być jedną z następujących wartości: **Mójkomputer**, **intranet**, **Zaufane**, **internetowe**lub **niezaufane**. Aby uzyskać więcej informacji dotyczących warunku członkostwa, zobacz <xref:System.Security.Policy.ZoneMembershipCondition> Klasa.|  
  
 Argument *flags* , który może być używany z opcjami **– addgroup** i **– chggroup** , jest określany przy użyciu jednego z następujących elementów.  
  
|Argument|Opis|  
|--------------|-----------------|  
|**-Opis** "*Opis*"|W przypadku użycia z opcją **– addgroup** określa opis grupy kodu do dodania. Jeśli jest używana z opcją **– chggroup** , określa opis grupy kodu do edycji. Argument *Description* musi być ujęty w cudzysłów.|  
|**-wyłączny** {**on**&#124;**off**}|Gdy jest ustawiona na wartość **on**, wskazuje, że tylko zestaw uprawnień skojarzony z dodawaną lub modyfikowaną grupą kodu jest brany pod uwagę, gdy jakiś kod pasuje do warunku członkostwa grupy kodów. Jeśli ta opcja jest ustawiona na **off**, Caspol. exe traktuje zestawy uprawnień wszystkich zgodnych grup kodu na poziomie zasad.|  
|**-levelfinal** {**on**&#124;**off**}|Gdy jest ustawiona na wartość **on**, wskazuje, że nie ma żadnego poziomu zasad poniżej poziomu, w którym występuje dodana lub zmodyfikowana grupa kodów. Ta opcja jest typowo używana na poziomie zasad komputera. Na przykład, jeśli flaga grupy kodu ustawiona będzie na poziom komputera i jakiś kod odpowiada warunkowi członkostwa grupy kodu, Caspol.exe nie oblicza ani nie stosuje zasad poziomu użytkownika dla tego kodu.|  
|**-Nazwa** "*Nazwa*"|W przypadku użycia z opcją **– addgroup** określa nazwę skryptu dla grupy kodu do dodania. W przypadku użycia z opcją **-chggroup** określa nazwę skryptu dla grupy kodu do edycji. Argument *name* musi być ujęty w cudzysłów. Argument *name* nie może rozpoczynać się od cyfry i może zawierać tylko znaki a-z, 0-9 i znak podkreślenia. Grupy kodu mogą być określane przez tę *nazwę* zamiast według ich etykiety liczbowej. *Nazwa* jest również bardzo przydatna dla celów związanych z obsługą skryptów.|  
  
## <a name="remarks"></a>Uwagi  
 Zasady zabezpieczeń są wyrażone za pomocą trzech poziomów zasad: zasady komputera, zasady użytkownika i zasady przedsiębiorstwa. Zestaw uprawnień otrzymanych przez zestaw jest określony przez przecięcie zestawów uprawnień dopuszczonych przez trzy poziomy zasad. Każdy poziom zasad jest reprezentowany przez hierarchiczną strukturę grup kodu. Każda grupa kodu posiada warunek członkostwa, który określa, jaki kod jest członkiem tej grupy. Nazwany zestaw uprawnień jest również skojarzony z każdą grupą kodu. Ten zestaw uprawnień określa uprawnienia, które spełniają warunek członkostwa, jakie środowisko uruchomieniowe przydziela kodowi. Hierarchia grup kodu ze skojarzonymi nazwanymi zestawami uprawnień definiuje i utrzymuje każdy poziom zasad zabezpieczeń. Aby ustawić poziom zasad zabezpieczeń, można użyć opcji **– User**, **-customuser**,- **Machine** i **-Enterprise** .  
  
 Aby uzyskać więcej informacji na temat zasad zabezpieczeń i sposobu, w jaki środowisko uruchomieniowe określa uprawnienia do przydzielenia kodu, zobacz [Zarządzanie zasadami zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odwoływanie się do grup kodu i zestawów uprawnień  
 Aby ułatwić odwoływanie się do grup kodu w hierarchii, opcja **-list** wyświetla listę z wcięciem grup kodu wraz z ich etykietami liczbowymi (1, 1,1, 1.1.1 itd.). Inne operacje wiersza polecenia przeznaczone dla grup kodu także używają etykiet liczbowych, aby odwołać się do określonej grupy kodu.  
  
 Odwołania do nazwanych zestawów uprawnień możliwe są przy użyciu ich nazw. Opcja **– list** wyświetla listę grup kodu, po których następuje lista nazwanych zestawów uprawnień dostępnych w tych zasadach.  
  
## <a name="caspolexe-behavior"></a>Zachowanie Caspol.exe  
 Wszystkie opcje z wyjątkiem **-s**[**ecurity**] {**on** &#124; **off**} Użyj wersji .NET Framework, z którą została zainstalowana Caspol. exe. Jeśli zostanie uruchomiony program Caspol. exe, który został zainstalowany z wersją *X* środowiska uruchomieniowego, zmiany dotyczą tylko tej wersji. Inne instalacje środowiska uruchomieniowego, jeśli są, nie zostaną uwzględnione. Jeżeli program Caspol.exe jest uruchamiany w wierszu poleceń poza katalogiem określonej wersji środowiska uruchomieniowego, narzędzie jest wykonywane w pierwszym katalogu wersji środowiska uruchomieniowego w ścieżce (zazwyczaj ostatnio zainstalowane środowisko uruchomieniowe).  
  
 Opcja **-s**[**ecurity**] {**on** &#124; **off**} jest operacją obejmującą cały komputer. Wyłączenie zabezpieczeń dostępu kodu przerywa sprawdzenia zabezpieczeń dla całego kodu zarządzanego i dla wszystkich użytkowników komputera. Jeżeli jest zainstalowanych wiele wersji platformy .NET Framework, to polecenie wyłączy zabezpieczenia dla każdej zainstalowanej wersji na komputerze. Mimo że opcja **-list** pokazuje, że zabezpieczenia są wyłączone, nic inaczej nie wskazuje innym użytkownikom, że zabezpieczenia zostały wyłączone.  
  
 Gdy użytkownik bez praw administracyjnych uruchamia Caspol. exe, wszystkie opcje odnoszą się do zasad na poziomie użytkownika, o ile nie określono opcji **-Machine** . Gdy administrator uruchamia program Caspol. exe, wszystkie opcje odnoszą się do zasad komputera, chyba że określono opcję **– User** .  
  
 W pliku Caspol. exe musi być przyznany odpowiednik uprawnienia **wszystko** ustawione na wartość funkcja. Narzędzie posiada mechanizm zabezpieczający, który uniemożliwia modyfikowanie zasad w sposób uniemożliwiający udzielenia Caspol.exe uprawnień, których potrzebuje do uruchomienia. Podczas próby zmiany ustawień program Caspol.exe powiadamia, że żądana zmiana zasad spowoduje awarię narzędzia i zmiana zasad zostanie odrzucona. Mechanizm ochronny można wyłączyć dla danego polecenia za pomocą opcji **– Force** .  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Ręczna edycja plików konfiguracji zabezpieczeń  
 Trzy pliki konfiguracji zabezpieczeń odnoszą się do trzech poziomów zabezpieczeń obsługiwanych przez Caspol.exe: jeden dla zasad komputera, jeden dla podanego użytkownika i jeden dla zasad przedsiębiorstwa. Te trzy pliki są tworzone na dysku tylko wtedy, gdy zasady komputera, użytkownika lub przedsiębiorstwa są zmienione za pomocą Caspol.exe. W razie potrzeby można użyć opcji **– Reset** w pliku Caspol. exe w celu zapisania domyślnych zasad zabezpieczeń na dysku.  
  
 W większości przypadków ręczna edycja plików konfiguracji zabezpieczeń nie jest zalecana. Jednak mogą pojawić się scenariusze, w których modyfikowanie tych plików może być konieczne, na przykład gdy administrator chce edytować konfigurację zabezpieczeń dla określonego użytkownika.  
  
## <a name="examples"></a>Przykłady  
 **-addfulltrust**  
  
 Zakłada, że zestaw uprawnień zawierający niestandardowe uprawnienie został dodany do zasad komputera. To uprawnienie niestandardowe jest implementowane `MyPerm.exe`w, `MyPerm.exe` i odwołuje `MyOther.exe`się do klas w. Oba zestawy muszą być dodane do listy zestawów o pełnym zaufaniu. Następujące polecenie dodaje `MyPerm.exe` zestaw do listy pełne zaufanie dla zasad komputera.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Następujące polecenie dodaje `MyOther.exe` zestaw do listy pełne zaufanie dla zasad komputera.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Następujące polecenie dodaje podrzędną grupę kodu do korzenia hierarchii grup kodu zasad komputera. Nowa grupa kodu jest członkiem strefy **Internet** i jest skojarzona z zestawem uprawnień **wykonywania** .  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Następujące polecenie dodaje podrzędną grupę kodu, która daje udział \\\netserver\netshare lokalnego intranetu.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Następujące polecenie dodaje `Mypset` zestaw uprawnień do zasad użytkownika.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Następujące polecenie zmienia zestaw uprawnień w zasadach użytkownika grupy kodu o etykiecie 1,2. do zestawu uprawnień **wykonywanie** .  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Następujące polecenie zmienia warunek członkostwa w domyślnych zasadach grupy kodów o nazwie 1.2.1. i zmienia ustawienie flagi **wyłącznej** . Warunek członkostwa jest zdefiniowany jako kod pochodzący ze strefy **Internet** , a flaga **wyłączna** jest włączona.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Następujące polecenie zmienia zestaw uprawnień o nazwie `Mypset` na zestaw uprawnień zawarty w. `newpset.xml` Należy zauważyć, że aktualne wydanie nie obsługuje zmiany zestawów uprawnień, które są używane przez hierarchię grup kodu.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 Poniższe polecenie powoduje, że grupa kodów głównych zasad użytkownika (etykieta 1) jest skojarzona z zestawem uprawnień o wartości **Nothing** . Uniemożliwia to uruchomienie programu Caspol.exe.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-Odzyskaj**  
  
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
  
 Następujące polecenie usuwa zestaw uprawnień **wykonywanie** z zasad użytkownika.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Następujące polecenie usuwa `Mypset` z poziomu zasad użytkownika.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Następujące polecenie wyświetla wszystkie grupy kodu zasad komputera, które `myassembly` należą do.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Następujące polecenie wyświetla wszystkie grupy kodu komputera, przedsiębiorstwa i określone niestandardowe zasady użytkownika, które `myassembly` należą do.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Następujące polecenie oblicza uprawnienia dla `testassembly` programu na podstawie poziomów zasad komputera i użytkownika.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
