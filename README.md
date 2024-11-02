# -showing-the-code-snippet-for-DELETE-test-case-
def test_delete_product(self):
    # Create a product to delete
    product = Product(name="DeleteTestProduct", category="CategoryY", available=True)
    product.save()
    
    # Send a DELETE request
    response = self.client.delete(f"/products/{product.id}")
    
    # Assert that the product was deleted
    assert response.status_code == 204
    assert Product.find(product.id) is None
