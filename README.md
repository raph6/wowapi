# World of Warcraft API Golang

This is a simple wrapper for the World of Warcraft API written in Go.

## Usage

Get your API Access here : https://develop.battle.net/access/clients

Installation
```sh
go get -u github.com/raph6/wowapi
```

Usage
```go
import "github.com/raph6/wowapi"

func main() {
    // API_CLIENT_ID, API_SECRET, region, lang
    // accepted region ->  us | eu | kr | tw | cn
    // accepted lang -> en_US | es_MX | pt_BR | en_GB | es_ES | fr_FR | ru_RU | de_DE | pt_PT | it_IT | zh_TW | ko_KR | zh_CN
    client, err := wowapi.NewClient("xx_API_CLIENT_ID_xx", "xx_API_SECRET_xx", "eu", "fr_FR")
    if err != nil {
        fmt.Println(err)
        return
    }

    // Realm, Name
    // realm must be slugified and name must be lowercase
    titles, err := client.CharacterTitles("kirin-tor", "vimdiesel")
    if err != nil {
        fmt.Println(err)
        return
    }
    fmt.Println(titles)
}
```

Available methods
```go
client.CharacterAchievementsStatistics(realm string, name string)
client.CharacterAchievements(realm string, name string)
client.CharacterAppearance(realm string, name string)
client.CharacterCharacterMedia(realm string, name string)
client.CharacterCharacterStatus(realm string, name string)
client.CharacterCollectionsHeirlooms(realm string, name string)
client.CharacterCollectionsMounts(realm string, name string)
client.CharacterCollectionsPets(realm string, name string)
client.CharacterCollectionsToys(realm string, name string)
client.CharacterCollections(realm string, name string)
client.CharacterEncountersDungeons(realm string, name string)
client.CharacterEncountersRaids(realm string, name string)
client.CharacterEncounters(realm string, name string)
client.CharacterEquipment(realm string, name string)
client.CharacterMythicKeystoneProfile(realm string, name string)
client.CharacterPvpSummary(realm string, name string)
client.CharacterPvpBracket(realm string, name string, pvpbracket string)
client.CharacterQuestsCompleted(realm string, name string)
client.CharacterQuests(realm string, name string)
client.CharacterSoulbinds(realm string, name string)
client.CharacterSpecializations(realm string, name string)
client.CharacterReputations(realm string, name string)
client.CharacterProfessions(realm string, name string)
client.CharacterInfo(realm string, name string)
client.CharacterHunterPets(realm string, name string)
client.CharacterStatistics(realm string, name string)
```

You can also use the client like this
```go
req, err := wowapi.Client("xx_API_CLIENT_ID_xx", "xx_API_SECRET_xx", "eu", "fr_FR")
...
body, err := req("/profile/wow/character/kirin-tor/vimdiesel/statistics")
...
var data interface{}
err = json.Unmarshal(body, &data)
...
fmt.Println(data)
```

Todo
- [ ] pvp_summary_test.go
- [ ] pvp_bracket_test.go
- [ ] hunter_pets_test.go
- [ ] soulbinds_test.go
- [ ] Raider.io API


## Tests

```sh
API_CLIENT_ID=xxxxx API_SECRET=xxxxx go test
```

## Links

Official documentation : https://develop.battle.net/documentation/world-of-warcraft