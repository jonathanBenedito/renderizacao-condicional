# Aula 04 - Renderização Condicional
📄 Link de acesso aos <a href="https://cord-delivery-7eb.notion.site/React-Avan-ado-0dd7bebfaf364c1f8544098923b060e5">resumos</a>. 

🖼 Link de <a href="https://majestic-youtiao-a4333a.netlify.app/">demonstração</a>.

```jsx
const CardsList = (props) => {
    return (
        <ul>
            {
                props.cards.map((card, index) => {
                    return (
                        <li key={index}>
                            <img src={card.image} alt={card.value} />
                        </li>
                    )
                })
            }
        </ul>
    )
}

const DeckOfCards = () => {

    const [deck, setDeck] = useState({
        cards: []
    })

    useEffect(() => {
        const fetchData = async () => {
            const deckId = await createDeck()
            const data = await getCards(deckId)

            setDeck({
                cards: data.cards
            })
        }
        fetchData()
    }, [])

    return (
        <section>
            { deck.cards.length > 0 ? <CardsList cards={deck.cards} /> : "Nenhuma card foi encontrada"} 
        </section>
    )

}
```
