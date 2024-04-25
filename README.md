// Définition de la classe représentant chaque élément
data class Element(val name: String, val value: Double)

// Fonction pour calculer le pourcentage de répartition
fun calculatePercentage(elements: List<Element>): Map<String, Double> {
    val total = elements.sumByDouble { it.value }
    val percentages = mutableMapOf<String, Double>()
    
    for (element in elements) {
        val percentage = (element.value / total) * 100
        percentages[element.name] = percentage
    }
    
    return percentages
}

// Exemple d'utilisation dans une classe de service Spring Boot
@Service
class RepartitionService {
    
    fun calculateAndPrintRepartition(elements: List<Element>) {
        val percentages = calculatePercentage(elements)
        for ((name, percentage) in percentages) {
            println("$name : $percentage%")
        }
    }
}
